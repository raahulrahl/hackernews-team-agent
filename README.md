<p align="center">
  <img src="https://raw.githubusercontent.com/getbindu/create-bindu-agent/refs/heads/main/assets/light.svg" alt="bindu Logo" width="200">
</p>

<h1 align="center">hackernews-team-agent</h1>

<p align="center">
  <strong>A multi-agent system that aggregates, curates, and analyzes trending HackerNews stories by coordinating specialized agents to fetch top posts, read full articles, enrich with web research, and produce structured summaries with links. Ideal for news aggregation platforms, trend analysis, content curation, and automated newsletters. Powered by real-time API data, web search, and article extraction.</strong>
</p>

<p align="center">
  <a href="https://github.com/raahulrahl/hackernews-team-agent/actions/workflows/main.yml?query=branch%3Amain">
    <img src="https://img.shields.io/github/actions/workflow/status/raahulrahl/hackernews-team-agent/main.yml?branch=main" alt="Build status">
  </a>
  <a href="https://img.shields.io/github/license/raahulrahl/hackernews-team-agent">
    <img src="https://img.shields.io/github/license/raahulrahl/hackernews-team-agent" alt="License">
  </a>
  <a href="https://www.bindus.directory/agent/49">
    <img src="https://img.shields.io/badge/bindus.directory-agent%2F49-blue" alt="Bindus Directory">
  </a>
</p>

---

## 📖 Overview

A multi-agent system that aggregates, curates, and analyzes trending HackerNews stories by coordinating specialized agents to fetch top posts, read full articles, enrich with web research, and produce structured summaries with links. Ideal for news aggregation platforms, trend analysis, content curation, and automated newsletters. Powered by real-time API data, web search, and article extraction.. Built on the [Bindu Agent Framework](https://github.com/getbindu/bindu) for the Internet of Agents.

**Key Capabilities:**
- 🔍 Fetches top stories from HackerNews API
- 📰 Reads and extracts full article content from URLs
- 🌐 Enriches stories with web search research
- 📊 Produces structured summaries with reference links

-> [Postman Collection link](https://raahul-1409c5b4-717533.postman.co/workspace/getbindu's-Workspace~44eb7cfe-a752-4114-8a1a-631395f07bf1/collection/50606358-17410b1f-7d94-4ba1-8881-530acc3f156a?action=share&creator=50606358)

---

## 🚀 Quick Start

### Prerequisites

- Python 3.12+
- [uv](https://github.com/astral-sh/uv) package manager
- API keys for OpenRouter and Mem0 (both have free tiers)

### Installation

```bash
# Clone the repository
git clone https://github.com/raahulrahl/hackernews-team-agent.git
cd hackernews-team-agent

# Create virtual environment
uv venv --python 3.12.9
source .venv/bin/activate  # On Windows: .venv\Scripts\activate

# Install dependencies
uv sync

# Configure environment
cp .env.example .env
```

### Configuration

Edit `.env` and add your API keys:

| Key | Get It From | Required |
|-----|-------------|----------|
| `OPENROUTER_API_KEY` | [OpenRouter](https://openrouter.ai/keys) | ✅ Yes |
| `MEM0_API_KEY` | [Mem0 Dashboard](https://app.mem0.ai/dashboard/api-keys) | If you want to use Mem0 tools |

### Run the Agent

```bash
# Start the agent
uv run python -m hackernews_team_agent

# Agent will be available at http://localhost:3773
```

### Github Setup

```bash
# Initialize git repository and commit your code
git init -b main
git add .
git commit -m "Initial commit"

# Create repository on GitHub and push (replace with your GitHub username)
gh repo create raahulrahl/hackernews-team-agent --public --source=. --remote=origin --push
```

---

## 💡 Usage

### Example Queries

```bash
# Get top AI stories
"What are the top AI stories on HackerNews today?"

# Analyze trending topics
"Summarize the top 5 trending stories on HackerNews"
```

### Input Formats

**Plain Text:**
```
What are the top stories about AI on HackerNews?
```

**JSON:**
```json
{
  "role": "user",
  "content": "Summarize the top 5 HackerNews stories"
}
```

### Output Structure

The agent returns structured output with:
- **title**: Article title
- **summary**: Comprehensive summary of the story
- **reference_links**: List of relevant URLs and sources

---

## 🔌 API Usage

The agent exposes a RESTful API when running. Default endpoint: `http://localhost:3773`

### Example Request

```bash
curl --location 'https://hackernews-team-agent.bindu-agents.bindus.directory' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <your-token>' \
--data '{
  "jsonrpc": "2.0",
  "method": "message/send",
  "params": {
    "message": {
      "role": "user",
      "parts": [
        {
          "kind": "text",
          "text": "Summarize the top 5 trending stories on HackerNews"
        }
      ],
      "kind": "message",
      "messageId": "550e8400-e29b-41d4-a716-446655440038",
      "contextId": "550e8400-e29b-41d4-a716-446655440038",
      "taskId": "550e8400-e29b-41d4-a716-446655440078"
    },
    "configuration": {
      "acceptedOutputModes": ["application/json"]
    }
  },
  "id": "550e8400-e29b-41d4-a716-446655440024"
}'
```

### Example Response

```json
{
  "jsonrpc": "2.0",
  "id": "550e8400-e29b-41d4-a716-446655440014",
  "result": {
    "id": "550e8400-e29b-41d4-a716-446655440078",
    "context_id": "550e8400-e29b-41d4-a716-446655440038",
    "kind": "task",
    "status": {
      "state": "completed",
      "timestamp": "2026-02-24T11:04:18.445630+00:00"
    },
    "history": [
      {
        "kind": "message",
        "role": "assistant",
        "parts": [
          {
            "kind": "text",
            "text": "Here's a summary of the current top 5 trending stories on HackerNews:\n\n1. **Terence Tao at 8 Years Old (1984)**\n   - Historical document about mathematical prodigy Terence Tao\n   - Currently trending with 281 points\n\n2. **Firefox 148's New AI Kill Switch Feature**\n   - Browser update introducing user control over AI features\n   - Allows disabling AI functionalities like chatbot prompts\n\n3. **enveil - Security Tool for .env Files**\n   - Tool to protect environment variables from AI coding assistants\n   - Uses AES-256-GCM encryption\n\n4. **Diode - Hardware Building Platform**\n   - Platform for building, programming, and simulating hardware\n\n5. **Distributed Queue in JSON File**\n   - Technical article about implementing distributed queue system"
          }
        ]
      }
    ],
    "artifacts": [
      {
        "name": "result",
        "parts": [
          {
            "kind": "text",
            "text": "Markdown formatted summary with numbered list of stories..."
          }
        ]
      }
    ]
  }
}
```

### Additional Resources

- 📖 [Full API Documentation](https://docs.getbindu.com/api-reference/all-the-tasks/send-message-to-agent)
- 📦 [Postman Collections](https://github.com/GetBindu/Bindu/tree/main/postman/collections)
- 🔧 [API Reference](https://docs.getbindu.com)

---

## 🎯 Skills

### hackernews-analysis (v1.0.0)

**Primary Capability:**
- Aggregates and analyzes HackerNews stories using a multi-agent team
- Coordinates HackerNews API, article reading, and web search

**Features:**
- Real-time HackerNews top stories retrieval
- Full article content extraction via Newspaper4k
- Web search enrichment via DuckDuckGo
- Structured output with Article model (title, summary, reference_links)

**Best Used For:**
- News aggregation and curation
- Trend analysis and monitoring
- Automated newsletter generation
- Content research and summarization

**Not Suitable For:**
- Real-time chat or conversation
- Non-HackerNews content analysis

**Performance:**
- Average processing time: ~10-30 seconds (depends on story count)
- Max concurrent requests: 10
- Memory per request: 256MB

---

## 🐳 Docker Deployment

### Local Docker Setup

```bash
# Build and run with Docker Compose
docker-compose up --build

# Agent will be available at http://localhost:3773
```

### Docker Configuration

The agent runs on port `3773` and requires:
- `OPENROUTER_API_KEY` environment variable
- `MEM0_API_KEY` environment variable

Configure these in your `.env` file before running.

### Production Deployment

```bash
# Use production compose file
docker-compose -f docker-compose.prod.yml up -d
```

---

## 🌐 Deploy to bindus.directory

Make your agent discoverable worldwide and enable agent-to-agent collaboration.

### Setup GitHub Secrets

```bash
# Authenticate with GitHub
gh auth login

# Set deployment secrets
gh secret set BINDU_API_TOKEN --body "<your-bindu-api-key>"
gh secret set DOCKERHUB_TOKEN --body "<your-dockerhub-token>"
```

Get your keys:
- **Bindu API Key**: [bindus.directory](https://bindus.directory) dashboard
- **Docker Hub Token**: [Docker Hub Security Settings](https://hub.docker.com/settings/security)

### Deploy

```bash
# Push to trigger automatic deployment
git push origin main
```

GitHub Actions will automatically:
1. Build your agent
2. Create Docker container
3. Push to Docker Hub
4. Register on bindus.directory

---

## 🛠️ Development

### Project Structure

```
hackernews-team-agent/
├── hackernews_team_agent/
│   ├── skills/
│   │   └── hackernews_team_agent/
│   │       ├── skill.yaml          # Skill configuration
│   │       └── __init__.py
│   ├── __init__.py
│   ├── __main__.py
│   ├── main.py                     # Agent entry point
│   └── agent_config.json           # Agent configuration
├── tests/
│   └── test_main.py
├── .env.example
├── docker-compose.yml
├── Dockerfile.agent
└── pyproject.toml
```

### Running Tests

```bash
make test              # Run all tests
make test-cov          # With coverage report
```

### Code Quality

```bash
make format            # Format code with ruff
make lint              # Run linters
make check             # Format + lint + test
```

### Pre-commit Hooks

```bash
# Install pre-commit hooks
uv run pre-commit install

# Run manually
uv run pre-commit run -a
```

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/amazing-feature`
3. Commit your changes: `git commit -m 'Add amazing feature'`
4. Push to the branch: `git push origin feature/amazing-feature`
5. Open a Pull Request

See [CONTRIBUTING.md](CONTRIBUTING.md) for detailed guidelines.

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🙏 Powered by Bindu

Built with the [Bindu Agent Framework](https://github.com/getbindu/bindu)

**Why Bindu?**
- 🌐 **Internet of Agents**: A2A, AP2, X402 protocols for agent collaboration
- ⚡ **Zero-config setup**: From idea to production in minutes
- 🛠️ **Production-ready**: Built-in deployment, monitoring, and scaling

**Build Your Own Agent:**
```bash
uvx cookiecutter https://github.com/getbindu/create-bindu-agent.git
```

---

## 📚 Resources

- 📖 [Full Documentation](https://raahulrahl.github.io/hackernews-team-agent/)
- 💻 [GitHub Repository](https://github.com/raahulrahl/hackernews-team-agent/)
- 🐛 [Report Issues](https://github.com/raahulrahl/hackernews-team-agent/issues)
- 💬 [Join Discord](https://discord.gg/3w5zuYUuwt)
- 🌐 [Agent Directory](https://bindus.directory)
- 📚 [Bindu Documentation](https://docs.getbindu.com)

---

<p align="center">
  <strong>Built with 💛 by the team from Amsterdam 🌷</strong>
</p>

<p align="center">
  <a href="https://github.com/raahulrahl/hackernews-team-agent">⭐ Star this repo</a> •
  <a href="https://discord.gg/3w5zuYUuwt">💬 Join Discord</a> •
  <a href="https://bindus.directory">🌐 Agent Directory</a>
</p>
