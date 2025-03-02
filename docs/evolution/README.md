# Evolution
- [Evolution journey](#evolution-journey)
  - [Key evolution points](#key-evolution-points)
  - [Visualise evolution](#visualise-evolution)
  - [Example](#example)
- [Attention is all you need](#attention-is-all-you-need)
- [Self attention vs attention](#self-attention-vs-attention)
## Evolution journey
- Evolution from Artificial Neural Networks (ANNs) to Transformers, highlighting the challenges faced at each stage and how they were addressed by the subsequent architecture:

| Architecture                     | Key Features                            | Challenges                                     | Solutions Provided by Next Architecture             |
|----------------------------------|-----------------------------------------|-----------------------------------------------|-----------------------------------------------------|
| **ANN**                          | Feedforward structure, no memory        | Cannot handle sequential data                  | Introduced RNNs to manage sequential data           |
| **RNN**                          | Handles sequential data, has memory     | Struggles with long-term dependencies (vanishing gradient problem) | LSTMs introduce memory cells and gates to handle long-term dependencies |
| **LSTM**                         | Memory cells, input/output/forget gates | Still processes data in a single direction     | Bidirectional RNNs process data in both directions, capturing more context |
| **Bidirectional RNN**            | Processes data forward and backward     | Limited in handling variable-length sequences and complex dependencies | Encoder-Decoder architecture separates encoding and decoding, adds flexibility |
| **Encoder-Decoder**              | Separate encoding and decoding phases, can handle variable-length sequences | Requires better focus on input sequence during decoding | Attention Mechanisms allow the decoder to focus on relevant parts of the input sequence |
| **Encoder-Decoder with Attention** | Dynamic focus on input sequence, improved context handling | Computational complexity, overfitting risk     | Transformer models introduce self-attention, scaling, and parallelization  |
| **Transformers**                 | Self-attention mechanism, parallel processing | Requires substantial computational resources, complex to train | Attention mechanisms scale effectively, simplifying training and improving performance |

### Key evolution points
1. **ANN to RNN**
   - **Challenge**: ANNs couldn't handle sequences effectively.
   - **Solution**: RNNs introduced `memory`, allowing `sequential data processing`.

2. **RNN to LSTM**
   - **Challenge**: RNNs struggled with long-term dependencies due to the vanishing gradient problem.
   - **Solution**: LSTMs introduced `memory cells and gates`, effectively `managing long-term dependencies`.

3. **LSTM to Bidirectional RNN**
   - **Challenge**: LSTMs processed data in a single direction, missing future context.
   - **Solution**: Bidirectional RNNs `processed data in both directions`, `capturing more context`.

4. **Bidirectional RNN to Encoder-Decoder**
   - **Challenge**: Bidirectional RNNs had limitations with variable-length sequences and complex dependencies.
   - **Solution**: Encoder-Decoder architectures `separated the encoding and decoding phases`, adding flexibility and `handling variable-length sequences`.

5. **Encoder-Decoder to Attention Mechanisms**
   - **Challenge**: Encoder-Decoder architectures needed a better focus mechanism on the input sequence during decoding.
   - **Solution**: Attention Mechanisms allowed the decoder to `dynamically focus on relevant parts` of the input sequence, `enhancing performance`.

6. **Attention Mechanisms to Transformers**
   - **Challenge**: Attention mechanisms, while powerful, introduce computational complexity and risk of overfitting.
   - **Solution**: Transformer models use `self-attention` mechanisms, enabling `scaling and parallel processing`, leading to breakthroughs in performance and efficiency.

### Visualise evolution
```
+---------+------------+-----------+-----------+-----------+------------+----------------------+
|  ANN    |   RNN      |   LSTM    | BiRNN     | Encoder   | Attention  | Transformer          |
|         |            |           |           | -Decoder  | Mechanisms | Models               |
|         |            |           |           |           |            |                      |
+---------+------------+-----------+-----------+-----------+------------+----------------------+
```

### Example
- The sentence we’ll be working with is "Tourists visit Finland to watch Northern lights."
- The accurate Finnish translation for this is "Turistit vierailevat Suomessa katsomassa revontulia."
- Now, let's see how different models handle this translation and how they evolve.

#### 1. Artificial Neural Network (ANN)
- **Problem**: ANNs are not ideal for sequence data because they lack the notion of time and order.
- They treat all inputs independently, which makes translating sentences that depend on the context and order challenging.

#### 2. Recurrent Neural Network (RNN)
- **Improvement**: RNNs introduced the concept of time steps, processing inputs sequentially.
- **Problem**: They struggle with long-term dependencies.
- For instance, remembering the context from "Tourists visit" and correctly linking it to "Northern lights" when generating the output.

#### 3. Long Short-Term Memory (LSTM)
- **Improvement**: LSTMs address the issue of long-term dependencies by maintaining a memory cell that can remember or forget information over long sequences.
- **Problem**: While better than RNNs, LSTMs can still struggle with very long sequences and are computationally intensive.

#### 4. Bidirectional RNN (BiRNN)
- **Improvement**: BiRNNs process the input data in both forward and backward directions, giving them access to past and future context.
- **Problem**: Although they improve context capture, they still inherit RNN's computational intensity and complexity.

#### 5. Encoder-Decoder
- **Improvement**: The Encoder-Decoder architecture separates the input processing (encoder) and output generation (decoder).
  - The encoder captures the input sentence in a context vector, and the decoder generates the output based on this vector.
  - Early 2010s, based on RNNs.
- **Problem**: The fixed-length context vector can bottleneck the model performance, especially for long sentences.

#### 6. Encoder-Decoder with Attention
- **Improvement**: Attention mechanisms allow the model to focus on different parts of the input sentence when generating each word of the output, alleviating the fixed context vector issue.
- **Problem**: Despite significant improvements, attention mechanisms can be complex to implement and computationally expensive.

#### 7. Transformer
- **Improvement**: Transformers use self-attention mechanisms and do not rely on sequential data processing, which makes them highly parallelizable and efficient.
- They capture long-range dependencies more effectively.
- 2017, based on self-attention mechanisms.
- **Result**: "Tourists visit Finland to watch Northern lights" is accurately translated to "Turistit vierailevat Suomessa katsomassa revontulia."

#### Conclusion
- Transformers represent the cutting-edge in sequence modeling, offering unparalleled efficiency and accuracy in translation tasks. Each model iteration builds on its predecessor, addressing critical weaknesses and evolving to handle the nuances of natural language more effectively.

## Attention is all you need
- "Attention Is All You Need" is a groundbreaking paper published by Vaswani et al. in 2017 that introduced the Transformer model, a novel architecture for handling sequence-to-sequence tasks, such as translation and text generation.
### Key Points
- **Self-Attention Mechanism**: The core innovation of the Transformer is the self-attention mechanism, which allows the model to weigh the importance of different words in a sequence relative to each other, capturing dependencies without relying on sequential processing.
- **Parallel Processing**: Unlike RNNs that process sequences step-by-step, the Transformer processes all elements of the sequence simultaneously, significantly speeding up training and improving efficiency.
- **Multi-Head Attention**: This technique enhances the model's ability to focus on different parts of the sequence concurrently, allowing it to capture various aspects of the context.
- **Positional Encoding**: Since the model processes inputs in parallel and loses the inherent order, positional encodings are added to retain the information about the position of words in the sequence.
- **Encoder-Decoder Structure**: The model consists of an encoder to process the input sequence and a decoder to generate the output sequence, both utilizing self-attention mechanisms.

### Impact
- The introduction of the Transformer model revolutionized the field of natural language processing (NLP), leading to significant improvements in tasks such as translation, summarization, and text generation. It paved the way for subsequent models like BERT, GPT-3, and T5, which have achieved state-of-the-art performance across various NLP benchmarks.

## Self attention vs attention
- Self-attention in Transformers is different from the traditional attention mechanism used in encoder-decoder architectures. 
- Here are the key differences

### Traditional Attention in Encoder-Decoder
- **Context Vector**: In traditional encoder-decoder models, attention mechanisms compute a context vector by weighing the importance of each encoder hidden state with respect to the current decoder state.
- **Dependency**: The attention mechanism relies on the relationship between the encoder's hidden states and the decoder's current state to generate the context vector.
- **Sequential Processing**: The decoder processes the output sequence step-by-step, utilizing the context vector at each step to generate the next token.
- **Attention Types**: Typically employs dot-product, additive, or scaled dot-product attention to calculate relevance scores between encoder and decoder states.

### Self-Attention in Transformers
- **Self-Contained Mechanism**: Self-attention **operates within both the encoder and the decoder**, allowing each word to attend to all other words in the same sequence, independent of position.
- **Positional Encoding**: Transformers include positional encodings to account for the `order of words` in the sequence, since self-attention itself is position-agnostic.
- **Parallel Processing**: Unlike traditional attention, self-attention processes all tokens in the sequence simultaneously, allowing for parallel computation and greater efficiency.
- **Multi-Head Attention**: Enhances the model's ability to focus on different parts of the sequence concurrently by using multiple attention heads.
- **Positional Encoding**: Since transformers process the sequence in parallel and do not inherently retain order information, positional encodings are added to the input embeddings to preserve positional information.
- **Layers**: Multiple layers of self-attention are stacked in the Transformer architecture, with each layer refining the representations learned in previous layers.

### Visual Comparison
- **Traditional Attention**: Focuses on the relationship between encoder states and decoder states, computing a context vector for each decoding step.
- **Self-Attention**: `Computes relationships` between all words in a sequence `simultaneously`, allowing each word to be represented with respect to the entire sequence context.

| Feature                        | Traditional Attention (Encoder-Decoder) | Self-Attention (Transformers)                  |
|------------------------------- |-----------------------------------------|------------------------------------------------|
| **Contextual Focus**           | Weighs encoder states based on decoder state | Each token attends to every other token       |
| **Processing Mode**            | Sequential                              | Parallel                                      |
| **Dependency Handling**        | Relies on encoder-decoder interaction    | Captures dependencies within the sequence     |
| **Complexity**                 | Limited by sequential dependencies       | Efficient with parallel processing            |
| **Enhancements**               | Dot-product/additive attention           | Multi-head attention, positional encoding     |
| **Application**                | Machine translation, seq-to-seq tasks    | NLP tasks like translation, summarization, and more|

### Summary
- **Traditional Attention**: Used in encoder-decoder models, focuses on encoder-decoder state interactions, processed sequentially.
- **Self-Attention**: Used in transformers, allows each token to attend to others within the sequence, enabling parallel processing and better handling of long-range dependencies.
