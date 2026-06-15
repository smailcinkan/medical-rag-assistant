\# Medical RAG Assistant



基于 LangChain + Streamlit 的医学知识 RAG 问答系统，支持多轮对话与文档溯源。



\## 核心流程



\*\*ask → review → answer\*\* 三步人机协同交互：



1\. \*\*Ask\*\*：用户提问，支持追问上下文拼接

2\. \*\*Review\*\*：展示检索文档片段，用户勾选可信内容

3\. \*\*Answer\*\*：DeepSeek 基于选中内容生成答案



\## 技术栈



| 模块 | 技术选型 |

|------|---------|

| 嵌入模型 | `BAAI/bge-m3` (768维) |

| 向量数据库 | Milvus |

| 重排序 | `BAAI/bge-reranker-base` (CrossEncoder) |

| 生成模型 | DeepSeek API (ChatOpenAI 兼容) |

| 文档清洗 | HTML/Markdown 双通道解析 (BeautifulSoup + Regex) |

| 文档切分 | RecursiveCharacterTextSplitter (chunk=500, overlap=50) |

| 前端 | Streamlit |



\## 项目结构

├── RAG.py          # 完整系统代码

├── requirements.txt

└── .gitignore



\## 快速开始



```bash

\# 1. 安装依赖

pip install -r requirements.txt



\# 2. 启动 Milvus（需提前安装 Docker）

docker run -d --name milvus -p 19530:19530 milvusdb/milvus



\# 3. 设置 API Key

export DEEPSEEK\_API\_KEY="your-key"



\# 4. 导入文档后启动

streamlit run RAG.py




