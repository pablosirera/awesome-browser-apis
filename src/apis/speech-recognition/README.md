---

title: Web Speech API 🗣
sidebar: auto

---

# Speech Recognition
> aka Voice to Text API

::: tip
Speech recognition is the ability of a machine or program to identify words and phrases in spoken language and convert them to a machine-readable format. Introduced in 2012 by W3C.
The HTML5 Speech Recognition API allows JavaScript to have access to a browser’s audio stream and to convert it to text.
:::

## Examples

### Demo #1
> Speech recognition example

<ClientOnly>
  <API-SpeechRecognition-Example1/>
</ClientOnly>

::: details Code
```js
if ('SpeechRecognition' in window) {
  // speech recognition API supported
} else {
  // speech recognition API not supported
}

const recognition = new SpeechRecognition()

recognition.onresult = (event) => {
  // What you said
  console.log(event.results[0][0].transcript)
}

// Start recognition
recognition.start()
```
:::

### Demo #2
> Speech recognition example

<ClientOnly>
  <API-SpeechRecognition-Example2/>
</ClientOnly>

::: details Code
```js
// Pages hosted on HTTPS do not need to ask repeatedly for permission, whereas HTTP hosted pages do
// Streaming results as they are received
// you can start to render results before the user has stopped talking

const recognition = new SpeechRecognition()

// Streaming "Realtime"
recognition.interimResults = true

// Max num of possible alternatives
recognition.maxAlternatives = 10

recognition.onresult = (event) => {
  // What you said
  console.log(event.results[0][0].transcript)
}

recognition.onstart = () => {
  isRecording = true
  console.log('Speech recognition service has started')
}

recognition.onend = () => {
  isRecording = false
  console.log('Speech recognition service has finished')
}

// ...

// Start recognition
recognition.start()
```
:::
