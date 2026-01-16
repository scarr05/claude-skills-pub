# Draw.io Diagram Skill for Claude

A Claude skill that enables AI-assisted creation of professional, editable draw.io diagrams. This skill teaches Claude how to generate valid `.drawio` XML files for architecture diagrams, flowcharts, network topologies, and technical illustrations.

## What is a Claude Skill?

Claude skills are structured prompts and reference materials that extend Claude's capabilities in specific domains. When this skill is loaded into Claude's context, it gains the ability to produce valid draw.io XML that can be opened directly in [draw.io](https://app.diagrams.net/) or diagrams.net.

## Features

- **Native draw.io XML output** — Files open directly in draw.io desktop or web app
- **Cloud provider icons** — AWS, Azure, and GCP official icon libraries
- **Architecture patterns** — Pre-built layouts for common diagram types
- **Customisable branding** — Easily adapt colours to match your organisation
- **Comprehensive reference** — Shapes, styles, arrows, and containers

## Quick Start

### For Claude.ai Users (Projects)

1. Create a new Claude Project
2. Add the skill files to your project's knowledge base:
   - `SKILL.md` (main skill file)
   - `references/` folder (all reference files)
3. Ask Claude to create diagrams:

```
Create an AWS architecture diagram showing a 3-tier web application 
with ALB, ECS, and RDS across two availability zones.
```

### For Claude API / Claude Desktop (MCP)

Add the skill files to your system prompt or use as reference materials in your prompts.

### For Anthropic Workbench

Paste the contents of `SKILL.md` into your system prompt, with reference files as needed.

## Repository Structure

```
drawio-skill/
├── SKILL.md                           # Main skill file (required)
├── README.md                          # This file
└── references/
    ├── architecture-patterns.md       # Common diagram layouts
    ├── branding.md                    # Company colour customisation
    ├── cloud-icons.md                 # AWS/Azure/GCP icon reference
    └── style-guide.md                 # Shapes, effects, and styling
```

## Example Outputs

The skill can generate diagrams for:

- **Cloud architecture** — Multi-region, multi-AZ deployments
- **DR/Replication flows** — Production to DR site with failover paths
- **Microservices** — Service mesh, API gateways, message queues
- **Network topology** — VPCs, subnets, hub-and-spoke networks
- **CI/CD pipelines** — Build, test, deploy stages
- **Data flows** — ETL pipelines, data lake architectures

## Customising for Your Organisation

### Adding Your Brand Colours

Edit `references/branding.md` to define your organisation's colours:

```markdown
## Your Brand Colors

Primary:    fillColor=#YOUR_PRIMARY;strokeColor=#YOUR_DARKER;fontColor=#FFFFFF
Secondary:  fillColor=#YOUR_ACCENT;strokeColor=#YOUR_DARKER;fontColor=#333333
```

**Example for "Acme Corp" (blue/orange brand):**

```markdown
## Acme Corp Brand Colors

Primary:    fillColor=#1E3A5F;strokeColor=#162d4a;fontColor=#FFFFFF
Secondary:  fillColor=#FF6B35;strokeColor=#cc552a;fontColor=#FFFFFF
Dark:       fillColor=#0D1B2A;strokeColor=#0D1B2A;fontColor=#FFFFFF
Light BG:   fillColor=#F0F4F8;strokeColor=#1E3A5F
```

### Calculating Stroke Colours

Stroke colours should be approximately 20% darker than fill colours for a professional look:

| Fill | Calculation | Stroke |
|------|-------------|--------|
| `#1E3A5F` | Multiply RGB by 0.8 | `#162d4a` |
| `#FF6B35` | Multiply RGB by 0.8 | `#cc552a` |

### Adding Company-Specific Patterns

If your organisation has standard diagram layouts, add them to `references/architecture-patterns.md`:

```markdown
## Acme Standard Architecture

### Customer Data Platform Layout

```
┌─────────────┐   ┌─────────────┐   ┌─────────────┐
│   Ingest    │──►│   Process   │──►│   Serve     │
│  (Kinesis)  │   │   (EMR)     │   │ (Redshift)  │
└─────────────┘   └─────────────┘   └─────────────┘
```
```

### Renaming for Your Organisation

Feel free to fork and rename this skill for internal use:

1. Fork the repository
2. Update references to match your company
3. Add your logo/branding to diagrams (via custom header patterns)
4. Share internally via your preferred method

## Using the Skill

### Basic Usage

```
Create a simple flowchart showing user login → authentication → dashboard
```

### With Cloud Icons

```
Create an Azure architecture diagram with:
- Application Gateway
- 2 VMs in an availability set
- Azure SQL Database
- Key Vault for secrets
```

### With Branding

```
Create a data flow diagram using our company branding for a 
customer onboarding process
```

### Complex Multi-Cloud

```
Create a hybrid architecture showing:
- On-premise VMware environment (left)
- AWS landing zone (center) 
- DR site in Azure (right)
Include VPN connections and data replication flows
```

## Tips for Best Results

1. **Be specific about layout** — "left to right", "three zones", "layered stack"
2. **Name your components** — Give Claude specific service names to label
3. **Specify cloud provider** — "AWS", "Azure", or "GCP" for correct icons
4. **Request legends** — "Include a legend explaining the color coding"
5. **Mention status** — "Show production as active (green) and DR as standby (grey)"

## Opening Generated Files

1. Claude will output a `.drawio` file
2. Download the file
3. Open with:
   - [draw.io Desktop](https://www.diagrams.net/) (recommended)
   - [draw.io Web](https://app.diagrams.net/)
   - VS Code with [Draw.io Integration](https://marketplace.visualstudio.com/items?itemName=hediet.vscode-drawio) extension

## Contributing

Contributions welcome! Areas that would benefit from expansion:

- Additional cloud provider icons (Oracle Cloud, IBM Cloud)
- Industry-specific patterns (healthcare, finance, retail)
- Integration with other diagramming tools
- Accessibility improvements

## Licence

MIT — Use freely, attribution appreciated.

## Acknowledgements

- [draw.io / diagrams.net](https://www.diagrams.net/) — Excellent free diagramming tool
- [AWS Architecture Icons](https://aws.amazon.com/architecture/icons/)
- [Azure Architecture Icons](https://docs.microsoft.com/en-us/azure/architecture/icons/)
- [GCP Architecture Icons](https://cloud.google.com/icons)

---

## Frequently Asked Questions

### Can I use this without Claude Projects?

Yes! Copy the contents of `SKILL.md` into your system prompt or include it as context in your messages. The reference files provide additional detail but aren't strictly required.

### Why XML instead of a visual editor?

Claude can't interact with visual editors, but it can generate structured XML. The draw.io XML format is well-documented and produces files that are fully editable in the draw.io application.

### How do I add icons not in the reference?

1. Open draw.io with the relevant icon library enabled
2. Drag the icon you want onto the canvas
3. Select it and press Ctrl+E (Cmd+E on Mac) to view the style
4. Copy the `resIcon=` or `image=` value
5. Add it to your local copy of `references/cloud-icons.md`

### Can Claude modify existing diagrams?

Yes, if you provide the XML content of an existing `.drawio` file, Claude can add elements, change styles, or reorganise the layout.

### What's the maximum diagram complexity?

Claude can handle diagrams with 50-100+ elements, though very complex diagrams may benefit from being built incrementally across multiple prompts.
