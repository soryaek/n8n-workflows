# n8n Workflows - Slack + Google Sheets Volunteer Management

A collection of n8n workflows that create an intelligent volunteer management system by integrating Slack with Google Sheets using AI-powered queries and automated responses.

[![n8n Workflow Demo](https://img.youtube.com/vi/39kpqIoT0tE/0.jpg)](https://youtu.be/39kpqIoT0tE)

## 🎯 **What This Project Does**

This automation system allows team members to:
- **Query volunteer information** through Slack using natural language
- **Get instant responses** about volunteer availability, contact details, and event participation
- **Update volunteer records** automatically in Google Sheets
- **Use AI-powered search** to find volunteers based on various criteria

## 🏗️ **Architecture Overview**

The system consists of three interconnected workflows:

### 1. **Volunteer Lookup** (Main Interface)
- **Trigger**: Slack app mentions and chat messages
- **AI Processing**: Uses OpenAI to understand natural language queries
- **Response**: Sends formatted volunteer information back to Slack
- **Integration**: Connects to Google Sheets via MCP (Model Context Protocol)

### 2. **Row Lookup** (Data Retrieval)
- **Purpose**: Searches Google Sheets for volunteer records
- **Input**: Column name and search value
- **Output**: Filtered volunteer data
- **Usage**: Called by other workflows to fetch information

### 3. **Google Sheet MCP** (Data Updates)
- **Purpose**: Updates volunteer information in Google Sheets
- **Trigger**: MCP server requests
- **Actions**: Modifies volunteer records (contact info, availability, etc.)
- **Integration**: Works with the Row Lookup workflow for data consistency

## 🚀 **Quick Start**

### Prerequisites
- n8n instance (self-hosted or cloud)
- Google Sheets with volunteer data
- Slack workspace with app permissions
- OpenAI API access

### 1. Import Workflows
Download and import the three JSON workflow files into your n8n instance.

### 2. Set Up Credentials
Create the following credentials in n8n:
- **Google Sheets OAuth2**: For accessing your volunteer spreadsheet
- **Slack API**: For Slack integration
- **OpenAI API**: For AI-powered query understanding

### 3. Configure Placeholder Values
Replace the placeholder variables in each workflow with your actual values:

#### Google Sheets Configuration
```json
"{{GOOGLE_SHEET_ID}}" → "Your actual Google Sheet document ID"
"{{GOOGLE_SHEETS_CREDENTIAL_ID}}" → "Your n8n Google Sheets credential ID"
```

#### Slack Configuration
```json
"{{SLACK_CHANNEL_ID}}" → "Your Slack channel ID (e.g., C09CPN5EY4U)"
"{{SLACK_CREDENTIAL_ID}}" → "Your n8n Slack credential ID"
"{{SLACK_WEBHOOK_ID}}" → "Your Slack trigger webhook ID"
"{{SLACK_SEND_WEBHOOK_ID}}" → "Your Slack send message webhook ID"
```

#### OpenAI Configuration
```json
"{{OPENAI_CREDENTIAL_ID}}" → "Your n8n OpenAI credential ID"
```

#### MCP Configuration
```json
"{{MCP_WEBHOOK_ID}}" → "Your MCP server webhook ID"
"{{MCP_ENDPOINT_URL}}" → "Your MCP endpoint URL"
"{{WORKFLOW_ID}}" → "The ID of your Row Lookup workflow"
```

#### n8n Instance
```json
"{{N8N_INSTANCE_ID}}" → "Your n8n instance ID"
```

### 4. Test the System
1. Activate all workflows
2. Send a message mentioning your Slack bot
3. Ask questions like "Who is available for the event this weekend?"
4. Verify responses and data updates

## 📊 **Expected Data Structure**

Your Google Sheet should have these columns:
- **ID**: Unique identifier for each volunteer
- **Full Name**: Complete name
- **First Name**: First name only
- **Last Name**: Last name only
- **Phone**: Contact number
- **Email**: Email address
- **Events**: Events they're signed up for
- **Manager**: Assigned manager
- **Active**: Current status (Active/Inactive)

## 💬 **Example Queries**

Users can ask questions like:
- "Who is John Smith?"
- "Show me all volunteers for the food drive"
- "Who is available this weekend?"
- "Update John's phone number to 555-1234"
- "List all active volunteers"

## 🔧 **Customization Options**

- **Add new columns** to the Google Sheet and update workflow schemas
- **Modify AI prompts** to handle different types of queries
- **Extend functionality** to other platforms (Discord, Teams, etc.)
- **Add validation rules** for data updates
- **Implement approval workflows** for sensitive changes

## 🛠️ **Troubleshooting**

### Common Issues
- **Credential errors**: Verify all credential IDs are correct
- **Webhook failures**: Check webhook URLs and permissions
- **Data not found**: Ensure Google Sheet column names match exactly
- **Slack permissions**: Verify bot has access to the specified channel

### Debug Steps
1. Check n8n execution logs
2. Verify all placeholder values are replaced
3. Test individual workflow nodes
4. Confirm API rate limits aren't exceeded

## 🤝 **Contributing**

We welcome contributions! When adding new workflows:
1. Use placeholder variables for all sensitive data
2. Include clear documentation
3. Test thoroughly before submitting
4. Follow the existing naming conventions

## 📚 **Resources**

- [n8n Documentation](https://docs.n8n.io/)
- [Google Sheets API](https://developers.google.com/sheets/api)
- [Slack API](https://api.slack.com/)
- [OpenAI API](https://platform.openai.com/docs)

## 🆘 **Support**

For issues or questions:
1. Check the troubleshooting section above
2. Review n8n community forums
3. Open an issue in this repository
4. Check the n8n documentation

---

**Note**: This system is designed for internal team use. Ensure compliance with your organization's data privacy policies and API usage guidelines. 