# Employee Similarity Search with ChromaDB

This project demonstrates how to build an **AI-powered employee similarity and metadata search system** using [ChromaDB](https://docs.trychroma.com/) and [SentenceTransformers](https://www.sbert.net/).  
It stores employee information, generates embeddings for semantic similarity search, and supports advanced filtering based on metadata (e.g., department, location, experience).  

---

## 🚀 Features
- **Employee Database in ChromaDB**  
  - Store structured employee data with metadata (role, department, skills, etc.).  
- **Embeddings with SentenceTransformers**  
  - Use the `all-MiniLM-L6-v2` model for efficient text vectorization.  
- **Similarity Search**  
  - Find employees based on semantic queries like _"Python developer with web development experience"_.  
- **Metadata Filtering**  
  - Query employees by department, location, or experience thresholds.  
- **Combined Search**  
  - Apply both similarity search and metadata filtering simultaneously.  

---

## 📂 Project Structure
.
├── main.py # Main script (this file)
├── requirements.txt
└── README.md


---

## ⚙️ Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/employee-similarity-search.git
   cd employee-similarity-search

2. Create a virtual environment (optional but recommended):
   
   python -m venv venv
   source venv/bin/activate   # On Mac/Linux
   venv\Scripts\activate      # On Windows

▶️ Usage

Run the main script:

python main.py


You’ll see:

A new employee collection created in ChromaDB.

Employee records inserted.

Example queries and metadata filtering results printed.   


🔍 Example Queries

Similarity Search
Find Python developers:

query_text = "Python developer with web development experience"
results = collection.query(query_texts=[query_text], n_results=3)


Metadata Filtering
Find all employees in Engineering:

results = collection.get(where={"department": "Engineering"})


Find employees with 10+ years experience:

results = collection.get(where={"experience": {"$gte": 10}})


Find employees in California (SF + LA):

results = collection.get(where={"location": {"$in": ["San Francisco", "Los Angeles"]}})


Combined Search
Find senior Python developers in major tech cities:

query_text = "senior Python developer full-stack"
results = collection.query(
    query_texts=[query_text],
    n_results=5,
    where={
        "$and": [
            {"experience": {"$gte": 8}},
            {"location": {"$in": ["San Francisco", "New York", "Seattle"]}}
        ]
    }
)

📊 Output Example
1. Searching for Python developers:
   Query: 'Python developer with web development experience'
   1. Alex Rodriguez (employee_10) - Distance: 0.1389
      Role: Lead Software Engineer, Department: Engineering
      Document: Lead Software Engineer with 18 years of experience in Engineering...

3. Finding all Engineering employees:
   Found 7 Engineering employees:
   - John Doe: Software Engineer (5 years)
   - Michael Brown: Senior Software Engineer (12 years)
   - ...

🧩 Next Steps

Extend the dataset with more employees and richer skills.

Build a REST API or Streamlit app for interactive queries.

Add support for resume search or job matching.
