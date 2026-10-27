# Rajesh Sripathi

Senior GenAI / Agentic AI Specialist Solutions Architect at AWS, based in London.

I design production agentic AI and LLM platforms for enterprise customers — mostly telco and
retail, mostly at scale. I'm interested in the parts that usually get skipped: how you authorise
an agent's tools, how you prove the system actually works, and what governance really costs you
in latency.

**Working depth:** multi-agent architectures (Strands, Bedrock AgentCore, LangGraph) · A2A and MCP ·
RAG and retrieval design · distributed training on SageMaker HyperPod / P5 · inference optimisation
and serving · agent authorisation, guardrails and threat modelling · LLM and agent evaluation

## Reference architectures — AWS Solutions Library

Published AWS reference architectures. Each carries AWS's *reviewed for technical accuracy* date,
which is AWS validating the design.

- **[Guidance for Visual Search on AWS](https://github.com/aws-solutions-library-samples/guidance-for-visual-search-on-aws)**
  — *first-named author.* Image-based product discovery for ecommerce: Titan Multimodal Embeddings
  and Claude 3 Sonnet over OpenSearch Serverless k-NN, fronted by API Gateway and Lambda, deployed
  by CDK. Ships the architecture, an 11-step request flow and a cost model.
  [Companion notebooks →](https://github.com/aws-samples/visual-search-for-retail-with-amazon-bedrock-and-amazon-opensearch-notebooks)
- **[Guidance for Analyzing Customer Conversations on AWS](https://docs.aws.amazon.com/solutions/analyzing-customer-conversations-on-aws/)**
  — *named author.* Contact-centre calls and chat transcripts to structured insight: Transcribe into
  Bedrock Claude 3 Sonnet for summarisation, dual-sided sentiment and action items, with DynamoDB
  persistence and threshold-triggered reporting. Reference architecture reviewed August 2024.
  [Repository →](https://github.com/aws-solutions-library-samples/guidance-for-analyzing-customer-conversations-on-aws)
- **[Web Store on AWS](https://docs.aws.amazon.com/solutions/web-store-on-aws/)**
  — headless ecommerce reference architecture spanning the frontend UI, backend services and seven
  core commerce capabilities: search, personalisation, marketing, fraud detection, customer
  authentication, location services and conversational support. Reference architecture reviewed
  January 2024.
- **[Target Marketing on AWS](https://docs.aws.amazon.com/solutions/target-marketing-on-aws/)**
  — geofenced, one-to-one retail marketing. Shoppers inside a store's geofence are identified by
  GPS or pre-installed in-store beacons and engaged with personalised recommendations and
  promotions over push notification, SMS and email — converting proximity into foot traffic.
  Reference architecture reviewed April 2024.

<sub>Dated PDF captures of these pages are in [`archive/`](archive/) — the live links above are
canonical.</sub>

## Reference implementations

- **[Multi-agent train travel assistant on Bedrock AgentCore](https://github.com/rasripa/rs-travelagent-langgraph-multiagent-with-evals)**
  — how to give three agents shared tool infrastructure without shared tool access. One gateway
  fronting three MCP servers with per-tool Cedar policies, so two agents calling the same endpoint
  see different tool lists; strict hub-and-spoke, a router holding zero tools, one IAM role per
  agent. A 31-case dual-judge evaluation harness then surfaced a cross-traveller data-disclosure
  gap the design hadn't closed — documented, not tuned away. Design decisions and rejected
  alternatives written up in full.
- **[Network operations agent](https://github.com/rasripa/rs-telco-network-ops)**
  — runbooks as data rather than prompt text. Each procedure ships a metadata sidecar so retrieval
  filters on metadata instead of leaning on semantic similarity, which means network operations can
  revise a procedure without anyone touching the agent. Tools arrive over MCP rather than inlined,
  and customer-facing output passes an explicit content guard — the riskiest thing the agent does
  gets a check of its own. Exact dependency pins and property-based tests.
- **[Handbook-grounded cell tower inspection](https://github.com/rasripa/rs-cell-tower-anomaly-detection)**
  — a vision model saying a tower looks "damaged" isn't an inspection result; citing the checklist
  item it fails is. The inspection handbook is loaded as context and findings are reported against
  its codes, so changing the handbook changes the findings with no code change. Four specialist
  agents behind a Strands orchestrator, over synthetic imagery generated with Nova Canvas and a
  checklist built from the public ANSI/TIA-222-G standard — each test image has a documented
  expected result, so it doubles as a small evaluation set.

## Publications — AWS Machine Learning Blog

- **[Transforming network operations with AI: how Swisscom built a Network Assistant using Amazon Bedrock](https://aws.amazon.com/blogs/machine-learning/transforming-network-operations-with-ai-how-swisscom-built-a-network-assistant-using-amazon-bedrock/)**
  — July 2025, co-authored with Swisscom. A supervisor agent over documentation and calculator
  sub-agents, Bedrock Knowledge Bases for retrieval, natural language to SQL via Athena on a
  serverless S3 data lake, and Guardrails on the boundary.
- **[Analyze customer reviews using Amazon Bedrock](https://aws.amazon.com/blogs/machine-learning/analyze-customer-reviews-using-amazon-bedrock/)**
  — August 2024, *first-named author.* Batch review analysis producing summaries, sentiment with
  confidence scoring and suggested product improvements, wired into automated reporting.
  [Code →](https://github.com/aws-samples/analyze-customer-reviews-through-amazon-bedrock)

## Workshops

Hands-on builds authored or maintained for AWS Workshop Studio, delivered by AWS field teams to
customer engineering audiences. Where a repository is linked, it is the self-paced version of the
same material.

<!-- Catalog URLs still to assign to the three unlinked entries below:
     https://catalog.us-east-1.prod.workshops.aws/workshops/27512c1c-fa03-4269-916e-570ece517631/en-US
     https://catalog.us-east-1.prod.workshops.aws/workshops/7ba881e7-12f1-4ce1-8225-ad8dd68e74fa/en-US
     https://catalog.us-east-1.prod.workshops.aws/workshops/d674f40f-d636-4654-9322-04dafc7cc63e/en-US -->

- **Multi-agent collaboration with MCP, Strands and Amazon Bedrock AgentCore**
  — maintainer and contributor; delivered at 200+ events. A build for architects, data scientists
  and ML engineers: an agentic assistant answering questions over a company's profile, policies
  and financial reporting, and making conversational product recommendations.
- **[Retail/CPG multi-agent with MCP, Strands and AgentCore](https://catalog.workshops.aws/retail-multi-agent-mcp-strands-agentcore/en-US)**
  — authored. Designed around three AgentCore deployment topologies (agents-as-tools → boto3
  invocation → A2A protocol) as a crawl/walk/run maturity model; delivered at 150+ events.
  [Labs and code →](https://github.com/rasripa/rs-agentic-ai-strands-agents-and-mcp-retail-cpg)
- **Auto ML pipeline for custom telco language models in Amazon Connect**
  — authored; delivered at re:Invent 2025 as IND337. End-to-end domain adaptation: Glue cataloguing
  the corpus, SageMaker fine-tuning Llama models trained on Trainium, Bedrock serving, and Amazon
  Connect integration via Lambda for telecom-specific responses and intent classification — with
  Nova Sonic for automated callbacks and a continuous-learning loop.
- **Kiro CLI: From Foundations to a Deployed AI Agent**
  — authored; published with public access so any AWS field team can deliver it without specialist
  support. A ground-up build covering steering, context management, custom agents and MCP
  integration, culminating in a billing assistant with a chat UI deployed to Bedrock AgentCore
  Runtime, then spec-driven development and multi-agent orchestration. No prior agent experience
  assumed.
- **[Debug LLM bottlenecks with NVIDIA Nsight](https://github.com/rasripa/rs-debug-llm-bottlenecks-with-nvidia-nsight)**
  — authored; delivered at re:Invent 2025 as AIM315. Profiling LLM training and inference pipelines
  on GPU infrastructure with Nsight to locate bottlenecks, then accelerating report analysis and
  comparison. Baseline/optimised notebook pairs plus 32 annotated Nsight timeline captures, so the
  diagnosis can be followed without a GPU.
- **[Building Intelligent Network Operations with Strands Agents and Amazon Bedrock AgentCore](https://github.com/rasripa/rs-agentic-ai-with-strands-and-bedrock-agentcore-telecom)**
  — authored; 25+ events. A telecom-focused build for architects, generative AI developers and ML
  engineers: implementing an agentic solution with Strands and deploying it to Bedrock AgentCore.
- **[GenAI workshop for peer AWS Solutions Architects](https://github.com/rasripa/gen-ai-workshop)**
  — July–August 2023, authored and delivered to the UKI Enterprise Retail SA team. Built before
  Amazon Bedrock was generally available: FLAN-T5-XXL and GPT-J-6B on SageMaker JumpStart
  endpoints, embeddings served from a second endpoint, retrieval assembled by hand with LangChain,
  and fine-tuning through the SageMaker training API. Kept as a snapshot of that stack rather than
  updated to the current one.

## Open source

- **Strands Agents SDK** — identified and specified non-streaming support for third-party model
  providers ([harness-sdk #1254](https://github.com/strands-agents/harness-sdk/issues/1254));
  native support shipped in `python/v1.45.0`
- **aws-samples/sagemaker-genai-hosting-examples** — authored the Qwen3-30B-A3B FP8 deployment and
  benchmarking notebook ([PR #213](https://github.com/aws-samples/sagemaker-genai-hosting-examples/pull/213))

[All merged pull requests →](https://github.com/search?q=author%3Arasripa+is%3Apr+is%3Amerged&type=pullrequests)

## Talks & industry events

- **NVIDIA GTC (GPU Technology Conference) 2026** — *Optimizing GenAI Workloads on AWS GPUs
  Using Kiro*
- **AWS Summit London 2025** — *[Streamline RAG and model evaluation with Amazon Bedrock](https://www.youtube.com/watch?v=6mA0s6iWCNw)* (recording)
- **AWS re:Invent 2025** — two hands-on workshops as speaker:
  - *AIM315 — Debug LLM bottlenecks with NVIDIA Nsight*; primary speaker, and led the
    implementation as well as the delivery
  - *IND337 — Auto ML pipeline for custom telco language models*; domain adaptation of an LLM for
    telco, with the accuracy gain demonstrated through a sample contact-centre application
- **Mobile World Congress (MWC) 2025**, Barcelona — the telecoms industry's flagship event;
  demonstrated LLM training and inference on Trainium2
- **AWS Summit London 2024** — *[Drive personalized CX using generative AI and Amazon Personalize](https://www.youtube.com/watch?v=1I866XnTlsc)* (AIM208, recording)
- **National Retail Federation (NRF) Big Show 2024**, New York — the retail industry's flagship
  event; demonstrated the retail store and personalisation experience, previously delivered at
  **AWS Summit London 2023**
- **AWS Deep Dive Days 2023** — *Conversational AI using Amazon Lex*
- Technical content **reviewer and bar raiser** for AWS re:Invent and AWS Summit London, 2025 and
  2026; technical content reviewer, AWS Summit London 2024

## Writing

<!-- Add posts as they publish. Repo + writeup pairs read strongest. -->

## Elsewhere

[LinkedIn](https://www.linkedin.com/in/rajeshsripathi/)

---

<sub>Views are my own.</sub>
