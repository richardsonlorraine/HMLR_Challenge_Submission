HMLR Data Science Challenge: Planning Decision Classifier
Project Overview 
This repository contains a solution for classifying anonymized historical planning decision notices and extracting key metadata: Application Numbers and Applicant Names.
The solution uses a hybrid approach:
Rule-based Classification: Categorizing documents (e.g., "Notice of Approval" vs "Register of Planning Charges") based on specific legal headers.
Regex Extraction: Using patterns to identify varied application number formats like 02/80/1609 or P/00/0759.
Named Entity Recognition (NER): Leveraging spaCy (en_core_web_trf) to identify applicants such as "Mr M Dale" or "My First Company Ltd.".
Repository Structure
main.py: The primary execution script.
src/processor.py: Contains the HMLRDocumentProcessor class logic.
requirements.txt: Lists necessary libraries (PyMuPDF, spacy, transformers).
analysis_report.md: A one-page summary of EDA, limitations, and future improvements.
Installation & Setup
Clone the repository:
   git clone <your-repo-link>
cd HMLR_Challenge_Submission
Install dependencies:
   pip install -r requirements.txt
python -m spacy download en_core_web_trf
Run the processor:
   python main.py --input data/anonymised_1.pdf
Data Insights (Sample Results) Based on the provided dataset, the tool identifies:
Document Type
Application No.
Applicant

Register of Planning Charges
02/80/1609
Mr. & Mrs. J. M Doe

Notice of Approval
P/00/0759
Mr M Dale

Approval of Details
P/98/0964
Mrs AM Stephens


Analysis & Limitations
Spatial Context: Some documents, like the North Devon District Council notice, store primary data on the "reverse" side, which requires multi-page context handling.
Entity Linking: In tabular documents (Page 1), multiple applicants and numbers exist; future iterations would use Table Parsing to link entities more accurately.
Scalability: While regex is effective for the current samples, a LayoutLM approach is recommended for wider UK council variations.

Repository Structure A clean structure ensures the HMLR team can run your code immediately.
HMLR_Challenge_Submission/
├── data/               # Place the anonymised 1.pdf here
├── src/
│   ├── processor.py    # The core logic (class-based)
│   └── utils.py        # Regex patterns and helper functions
├── main.py             # Entry point to run the code
├── requirements.txt    # List of dependencies
├── analysis_report.md  # Your one-page analysis
└── README.md           # Instructions on how to setup and run
