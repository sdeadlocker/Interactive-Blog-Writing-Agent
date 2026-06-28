# 📝 Interactive Blog Writing Agent

An AI-powered **multi-agent blog generation system** built with **LangGraph**, **LangChain**, and **OpenAI**. The workflow automatically decides whether web research is required, generates a structured blog plan, writes sections in parallel, synthesizes the final article, and optionally generates technical diagrams using **Gemini Image Generation**.

## Features

- 🔀 Intelligent routing to determine if web research is needed
- 🌐 Automatic web research using Tavily
- 📋 AI-generated blog outline with structured tasks
- ⚡ Parallel section generation using LangGraph fan-out/fan-in
- 📚 Evidence-grounded content with citations
- 🖼️ Automatic technical diagram planning and generation
- 📝 Produces publication-ready Markdown blogs
- 🔄 Modular multi-agent architecture

## Workflow

```text
                ┌──────────────┐
                │ User Topic   │
                └──────┬───────┘
                       │
                 Router Agent
                       │
          ┌────────────┴────────────┐
          │                         │
   No Research               Web Research
          │                         │
          └────────────┬────────────┘
                       │
             Orchestrator Agent
                       │
          Parallel Section Writers
                       │
               Merge Content
                       │
             Image Planning Agent
                       │
          Gemini Image Generation
                       │
          Final Markdown Blog (.md)
```

## Tech Stack

- Python
- LangGraph
- LangChain
- OpenAI GPT-4.1 Mini
- Tavily Search API
- Gemini 2.5 Flash Image
- Pydantic
- dotenv

## Project Structure

```
├── main.py
├── images/
├── .env
├── requirements.txt
└── README.md
```

## Environment Variables

Create a `.env` file with:

```env
OPENAI_API_KEY=your_openai_key
TAVILY_API_KEY=your_tavily_key
GOOGLE_API_KEY=your_google_key
```

## Installation

```bash
git clone <repo-url>
cd Interactive-Blog-Writing-Agent

pip install -r requirements
```

## Usage

```python
result = app.invoke({
    "topic": "Agentic AI in Healthcare",
    "as_of": "2026-06-28"
})

print(result["final"])
```

## Example Output

- Research-backed technical blog
- Markdown file (`blog_title.md`)
- Generated technical diagrams in `images/`
- Embedded citations and images

## Multi-Agent Architecture

| Agent | Responsibility |
|--------|----------------|
| Router | Determines research strategy |
| Research | Collects and filters web evidence |
| Orchestrator | Creates blog outline and tasks |
| Worker | Writes individual sections in parallel |
| Reducer | Merges sections into a complete blog |
| Image Planner | Decides where diagrams improve understanding |
| Image Generator | Generates and embeds technical diagrams |

## Future Enhancements

- Support multiple LLM providers
- Human-in-the-loop editing
- SEO optimization
- Export to HTML/PDF
- Streaming generation
- Vector database integration for private knowledge
- Multi-language blog generation

## License

MIT License
