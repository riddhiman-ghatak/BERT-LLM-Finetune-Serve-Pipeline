
# BERT-LLM Classification Fine-Tuning and Serving Pipeline

This repository provides a complete pipeline for fine-tuning a BERT-based large language model (LLM) on a classification task and serving the trained model for inference. The project is designed to be flexible and can be run locally or adapted for cloud workflows.

## Features
- End-to-end pipeline for text classification using BERT or similar LLMs
- Modular code for data loading, model training, and inference
- Example notebook for interactive experimentation
- CLI support for training and serving

## Getting Started

### Clone the Repository
```bash
git clone <your-repo-url>
cd BERT-LLM-Finetune-Serve-Pipeline
```

### Install Dependencies
Install the required Python packages:
```bash
pip install -r requirements.txt
```

### Run the Tutorial Notebook
You can explore the pipeline and experiment interactively using the provided Jupyter notebook:
```bash
jupyter notebook tutorial.ipynb
```

## Usage

### Training the Model
To train the model from the command line, run:
```bash
# Example: Train with 3 epochs and full fine-tuning
python workflows/train_pipeline.py --epochs 3 --tuning_method full
```
You can adjust the arguments as needed (see the script for available options).

### Serving the Model
To serve the trained model for inference:
```bash
python app.py
```
This will start a local server (see `app.py` for details on endpoints and usage).

## Project Structure

- `app.py` - Script to serve the trained model via an API
- `tasks/` - Modules for data handling, model definition, and inference logic
- `workflows/` - Training and batch inference pipelines
- `tutorial.ipynb` - Interactive notebook for step-by-step guidance
- `requirements.txt` - List of required Python packages

## Customization
- You can modify the data loading and preprocessing logic in `tasks/data.py`.
- Model architecture and training parameters can be adjusted in `tasks/model.py` and `workflows/train_pipeline.py`.
- Inference logic can be customized in `tasks/inference.py` and `app.py`.

## License
This project is licensed under the terms of the LICENSE file in this repository.

## Acknowledgements
This project is inspired by best practices in NLP model fine-tuning and serving. See the notebook and code comments for further references.

### Install dependencies
```bash
pip install -r requirements.txt
```

### Authenticate to Union from CLI
After you have signed up for Union, you can authenticate to Union from the CLI.

If on Union Serverless
`union create login --serverless --auth device-flow`

If on Union BYOC (Bring Your Own Cloud)
`union create login --host <union-host-url>`

Now your environment is setup to run the project on remotely Union.

- [Autneticatoin docs](https://docs.union.ai/serverless/api-reference/union-cli#configure-the-union-cli)

### Run through the tutorial notebook or run the pipeline from CLI.
The tutorial notebook will guide you through the steps to fine-tune a BERT-LLM model on a classification task and serve the model using Union AI.

```bash
jupyter notebook tutorial.ipynb
```

Or you can run the steps for the training pipeline and serving from the CLI.

Train the model:
```bash
# 🌟 Run the bert training pipeline using lora, qlora or full
union run --remote workflows/train_pipeline.py train_pipeline --epochs 3 --tuning_method full 
```

Serve the model:
```bash
union deploy apps app.py bert-sentiment-analysis
```


