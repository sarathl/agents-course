# Unit 1

## What are LLMs?
LLM is an AI model which understands and generates human language. They are trained on vast amounts of data. They are usually built with Transformer architecture.

### What is a Transformer?
    Transformer is a deep learning architecture based on "Attention".
    Attention is all you need: This mechanism gives more "attention" or importance to more relevant words for next word prediction
        Eg: The words "france" and "capital" carry more weightage in predicting next word for "The capital of france is"

### Types of Transformers
There are 3 types of Transformers:

#### 1. Encoder
- Encoder based transformer takes text as input and outputs embeddings
- Example: BERT
- Uses: Text classification, sentiment analysis etc

#### 2. Decoder
- Decoder based transformer generates new tokens (given input tokens) to complete a sequence, one token at a time
- Example: LLaMA, most of the LLMs
- Uses: Chatbots, text and code generation

#### 3. Seq2Seq
- Combines an encoder and a decoder
- First encoder transforms input text to contextual representation and decoder generates the output text
- Example: BART
- Uses: Summarization, translation etc

### Working Principle
    The underlying principle of LLMs is to predict the next token given a series of previous tokens. LLMs are auto-regressive, output from one pass becomes input of the next pass. LLM generates the next token (given the previous set of tokens) until it predicts the next token to be EOS.

- #### How LLM works in short
    - Input text given is tokenized and the model computes a representation of the sequence which captures the meaning and position of each token in the sequence.
    - Model uses the representation generated to get a likelihood of each token in its vocabulary being the next token
    - Easiest decoding strategy is to take the token with maximum likelihood
        - Other advanced decoding strategies such as beam search exist (picking the token that maximizes total score even if individual token scores are less)
    - Repeat the process until EOS token is predicted. 


### LLMs Training
    LLMs are trained on large datasets of text, they learn to predict the next word in a sequence through self-supervising or masked language model objective (predict the missing words in a text)


## Messages and Special Tokens

### Chat Templates:
    Chat templates act as a bridge between conversational messages and specific formatting requirements for LLMs.
    
#### System Messages:
    System prompts define how a model should behave. They serve as persistent instructions, guiding every subsequent interaction.
    
    system_message = {
        "role": "system",
        "content": "You are a professional customer service agent. Always be polite, clear, and helpful."
    }

#### Conversations: User and Assistant Messages
    Conversation = alternating messages between a human (user) and an LLM (assistant)

    conversation = [
        {"role": "user", "content": "I need help with my order"},
        {"role": "assistant", "content": "I'd be happy to help. Could you provide your order number?"},
        {"role": "user", "content": "It's ORDER-123"},
    ]

    Chat templates help in structuring this conversation and sending it to the llm to maintain the context by storing the previous messages.