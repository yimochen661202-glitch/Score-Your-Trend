# Score-Your-Trend
An AI-powered cultural trend scoring tool that evaluates trends against brand-specific identity and marketing objectives, then turns relevant trends into ready-to-run activation plans.

## Project Status

🚧 Active development — academic project at USC Annenberg School for Communication and Journalism (PR-499).

## Problem

Brand social media teams spend 2–3 hours daily scanning trend signals across TikTok, Reddit, and Google Trends. Most of what surfaces is irrelevant noise to their specific brand. By the time a yes/no decision gets made, the trend window has often closed. Current solutions (paid agency social listening, generic trend dashboards) are slow, expensive, and not brand-specific.

## Solution Architecture

Four-layer system:

### 1. Brand DNA Layer
Stores brand-specific scoring context:
- Brand pillars (3–5 non-negotiable traits)
- Tone of voice
- Target audience profile
- Current marketing objectives
- Brand permissions and guardrails
- Historical trend decisions (logged over time)

### 2. Scraping Layer
Retrieves publicly available trend signals via official APIs:
- Reddit (via Reddit API)
- TikTok trend data
- Google Trends
- Both broad scans and hashtag/keyword-targeted retrieval

### 3. Scoring Layer
LLM-based relevance evaluation against brand DNA:
- Demographic match
- Tone match
- Risk assessment
- Strategic objective alignment
- Outputs a 0–100 fit score with reasoning

### 4. Activation Layer
Generates next-step recommendations:
- For high-fit trends: activation plan (angle, creator shortlist, timing window)
- For low-fit trends: defense note for leadership (competitor-fit logic, historical precedent)

## Tech Stack

- **Build environment:** Claude, Cursor
- **Backend:** Node.js
- **LLM:** Anthropic Claude API for scoring and generation
- **Data sources:** Reddit API, TikTok trend data, Google Trends

## Reddit API Usage

This project uses the Reddit API in **read-only** mode to retrieve publicly available posts and comments from a small, defined set of public subreddits relevant to brand-side cultural research.

- **Read-only:** No posting, commenting, voting, or any write operations
- **Public data only:** No private or NSFW subreddits
- **Rate-limit compliant:** Respects all Reddit API rate limits per official guidelines
- **No user data storage:** Does not retain user-identifying information

Subreddits accessed include (non-exhaustive): r/skincareaddiction, r/beautyaddiction, r/femalefashionadvice, r/sneakers, r/marketing, r/advertising.

## Workflow Integration

The tool is designed to plug into agency or brand workflows with clear human-in-the-loop handoffs:

| Step | Owner | Action |
|------|-------|--------|
| 0. Brand DNA Input | Brand Director | One-time setup + quarterly refresh |
| 1. Overnight Scanning | Tool (automated) | Retrieves and pre-scores trends |
| 2. Morning Review | Social Media Manager | 15-min review of ranked briefing |
| 3. Activation / Pass | Tool + SMM | Generates activation plan or defense note |
| 4. Execution | Junior Coordinator → SMM | Drafts content from plan |
| 5. Logging | Tool (automated) | Decision and reasoning logged to brand memory |

## Author

Yimo Chen, USC Annenberg School for Communication and Journalism, PR-499.

## Contact

For questions, code review access, or research collaboration: yimochen@usc.edu

## License

This project is currently a private academic prototype. Not licensed for redistribution.
