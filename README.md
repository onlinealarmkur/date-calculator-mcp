# Date Calculator

An MCP server for date calculations and public holidays, using the same [date calculator](https://onlinealarmkur.com/date/en/) created by Online Alarm Kur.

This repository contains documentation and registration metadata for the hosted service.

- **Endpoint:** `https://mcp.onlinealarmkur.com/`
- **Transport:** Streamable HTTP
- **Authentication:** None
- **Documentation:** [mcp.onlinealarmkur.com](https://mcp.onlinealarmkur.com/)

## Tools

| Tool | What it does |
| --- | --- |
| `count_days` | Count days between two dates, optionally excluding selected weekdays and public holidays. |
| `shift_date` | Add or subtract years, months, weeks and days, with optional weekday and holiday exclusions. |
| `get_holidays` | List public holidays, including observed dates, for a country and optional region, for up to 11 years per request. |
| `list_locations` | Find supported countries, regions and available years. |

Dates use the Gregorian calendar in `YYYY-MM-DD` format, without a time of day. Weekends and holidays are included unless explicitly excluded.

Date calculation results include the rules used and a share link that opens the same calculation on the website. Calculation and holiday tools accept the website's 32 languages; holiday names may fall back to their native language.

## Connect

### Claude

1. Open **Customize**, then **Connectors**.
2. Select **+ Add**, then **Add custom connector**.
3. Enter **Date Calculator** as the name and `https://mcp.onlinealarmkur.com/` as the URL, then select **Continue**.
4. Under **Authentication**, choose **No sign in**, then select **Add**.

On Team and Enterprise plans, an organization owner adds the connector first; members then connect it. See Anthropic's [custom connector instructions](https://support.claude.com/en/articles/11175166-get-started-with-custom-connectors-using-remote-mcp).

### Claude Code

```bash
claude mcp add --transport http date-calculator https://mcp.onlinealarmkur.com/
```

### Cursor

Add this entry to `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "date-calculator": {
      "url": "https://mcp.onlinealarmkur.com/"
    }
  }
}
```

### VS Code

Add this entry to `.vscode/mcp.json`:

```json
{
  "servers": {
    "date-calculator": {
      "type": "http",
      "url": "https://mcp.onlinealarmkur.com/"
    }
  }
}
```

If the configuration file already contains other servers, add the entry to the existing object.

### ChatGPT

Where your account and workspace allow custom MCP connections:

1. Open [ChatGPT Plugins](https://chatgpt.com/plugins) in your browser.
2. Select the plus button, then **Add custom MCP server**.
3. Enter **Date Calculator** as the name and `https://mcp.onlinealarmkur.com/` as the server URL. Choose no authentication.
4. Review the permissions and warning, then select **Create as a plugin**.
5. Install the resulting plugin, start a new conversation and select it using `@`.

See OpenAI's [custom MCP server instructions](https://developers.openai.com/plugins/deploy/connect-chatgpt).

### Grok

1. Open [Grok Connectors](https://grok.com/connectors).
2. Select **New Connector**, then **Custom**.
3. Enter `https://mcp.onlinealarmkur.com/` as the MCP server URL. No authentication is required by this server.
4. Complete the setup to make the tools available in conversations.

For Grok Business and Enterprise, a team admin must first add the connector for the organization.

See Grok's [connector documentation](https://docs.x.ai/grok/connectors).

### Other MCP clients

Where custom remote MCP connections are available, use `https://mcp.onlinealarmkur.com/` with Streamable HTTP and no authentication. See the [connection instructions](https://mcp.onlinealarmkur.com/).

## Example prompts

- "How many working days are there between 2 November and 24 December 2026 in Germany, excluding Saturdays, Sundays and public holidays?"
- "What date is 90 days after 15 January 2027?"
- "List the public holidays in Turkey for 2027."

## Limits

Rate limits apply. Holiday lookups share a daily budget; if it is exhausted, holiday features pause until 00:00 UTC. Calculations without holidays remain available.

Future holiday dates can change. Check important deadlines with the relevant authority.

## Support

For bug reports and questions, [open an issue](https://github.com/onlinealarmkur/date-calculator-mcp/issues).
Report security problems privately with [Report a vulnerability](https://github.com/onlinealarmkur/date-calculator-mcp/security/advisories/new).

- [MCP Documentation](https://mcp.onlinealarmkur.com/)
- [Privacy Policy](https://onlinealarmkur.com/privacy/en/)
- [Terms of Service](https://onlinealarmkur.com/terms/en/)
