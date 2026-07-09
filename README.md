# Client Portfolio News Impact Detection with AI & Gmail

This workflow automatically fetches the latest business news, analyzes its impact on clients using AI and sends alerts for high-impact articles while logging all processed data in Google Sheets. It ensures no duplicate processing using URL normalization and maintains a complete audit trail.

### Quick Implementation Steps

1. Add your **News API key** in the HTTP Request node in your n8n account.
2. Connect **Google Sheets** (Client Dataset + Article Log).
3. Configure **Gemini AI credentials**.
4. Set up **Gmail node** for alerts.
5. Activate the workflow (runs daily at 8 AM).

## What It Does

This workflow continuously monitors business news and evaluates its relevance to a predefined client dataset. It fetches the latest articles, validates them and ensures that only new articles are processed by comparing normalized URLs against previously logged entries.

Each article is enriched with structured client data and sent to an AI model for classification. The AI determines the impact level (High, Medium, Low) and identifies which clients are affected along with precise reasoning.

High-impact articles trigger automated email alerts, ensuring timely communication. All articles—regardless of impact—are logged in a Google Sheet along with metadata such as processing time, impact level, affected clients and email status.

## Who It's For

- Financial advisors and wealth managers
- Investment research teams
- Portfolio managers
- Risk analysis professionals
- Businesses tracking market impact on clients

## Requirements

- [**n8n account (Self-hosted or Cloud)**](https://n8n.partnerlinks.io/om1efg2qgvwi)
- **News API key** (https://newsapi.org/)
- **Google Sheets account** (2 sheets required)
  - Client Dataset
  - Article Processing Log
- **Google Gemini API credentials**
- **Gmail account** (for sending alerts)

## How It Works & Setup

### Step 1: Trigger Setup

- Configure the **Schedule Trigger** to run daily at 8 AM.

### Step 2: News API Configuration

- Add your API key in the **Fetch Latest Finance News** node.
- Ensure category is set to `business`.

### Step 3: Google Sheets Setup

- **Sheet 1: Client Dataset**
  - Must include fields like Client Name, Holdings, Sector Exposure, etc.

- **Sheet 2: Article Processing Log**
  - Stores processed articles with status and timestamps.

### Step 4: Client Data Preparation

- The workflow converts raw sheet data into structured arrays for AI processing.

### Step 5: Deduplication Logic

- Previously processed article URLs are normalized and stored.
- New articles are compared against this list to avoid duplicates.

### Step 6: AI Configuration

- Configure **Google Gemini (`gemini-2.5-flash`)** credentials.
- Ensure JSON output format is enabled.

### Step 7: Email Setup

- Configure Gmail node with recipient email.

### Step 8: Workflow Execution Flow

1. Fetch news articles
2. Validate and split articles
3. Process one article at a time
4. Check for duplicates
5. Attach client dataset
6. Send to AI for classification
7. Filter high-impact results
8. Send email alerts (if high impact)
9. Log all articles
10. Wait 1 minute before next article

## How To Customize Nodes

- **News API Node:** Change category or add keywords
- **AI Prompt:** Modify classification rules or output structure
- **Filter Node:** Adjust logic (e.g., include Medium impact)
- **Email Node:** Customize email format or recipients
- **Google Sheets:** Add more client attributes for deeper analysis

## Add-ons

- Slack or WhatsApp alerts instead of email
- Dashboard visualization (Google Data Studio / Power BI)
- Multi-language news support
- Sentiment analysis layer
- Priority scoring for clients

## Use Case Examples

- Alerting financial advisors about market-moving news
- Monitoring sector-specific risks for portfolios
- Identifying geopolitical risks affecting investments
- Automating daily research summaries
- Tracking impact of global events on client portfolios

There can be many more use cases depending on how the workflow is extended.

## Troubleshooting Guide

| Issue | Possible Cause | Solution |
|--------|----------------|----------|
| No articles fetched | Invalid API key | Verify News API key |
| Workflow stops early | Empty articles array | Check API response |
| Duplicate articles processed | URL normalization mismatch | Verify normalization logic |
| AI output error | Invalid JSON response | Ensure strict JSON prompt |
| Emails not sent | Gmail not configured | Reconnect Gmail credentials |
| Clients not mapped | Incorrect sheet structure | Validate column names |

## Need Help?

If you need help customizing this workflow, automating your recruitment processes, or integrating it with your HR systems, our **WeblineIndia** team is ready to assist. Explore our **[Process Automation Solutions](https://www.weblineindia.com/process-automation-solutions.html)** or connect with our **[n8n workflow development experts](https://www.weblineindia.com/n8n-automation/)** to build, customize, and scale your business automation with confidence.
