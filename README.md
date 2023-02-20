# GPT-3-Encoder-lambda
Javascript BPE Encoder Decoder for GPT-2 / GPT-3 with AWS Lambda compatibility

This lib can be used either with AWS Lambda or with any other "standard" node runtime / deployment
## Motivation
This is an adaptation of GPT-3-Encoder, the original repo could be found [here](https://github.com/latitudegames/GPT-3-Encoder).<br/>
As AWS lambda bundles the sources in one single JS file, the vocab.bpe & encoder.json file cannot be read using `fs.readFileSync(...)` as it's the case in the original implementation  

## About
GPT-2 and GPT-3 use byte pair encoding to turn text into a series of integers to feed into the model. This is a javascript implementation of OpenAI's original python encoder/decoder which can be found [here](https://github.com/openai/gpt-2)

## Install with npm

```
npm install gpt-3-encoder-lambda
```

## Usage

Compatible with Node >= 12

```js
const {encode, decode} = require('gpt-3-encoder-lambda')

const str = 'This is an example sentence to try encoding out on!'
const encoded = encode(str)
console.log('Encoded this string looks like: ', encoded)

console.log('We can look at each token and what it represents')
for(let token of encoded){
  console.log({token, string: decode([token])})
}

const decoded = decode(encoded)
console.log('We can decode it back into:\n', decoded)

```


