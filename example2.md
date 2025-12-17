# APIs and GitHub
## Text-to-speech API
API is short for Application Programming Interface. There are multiple APIs available on GitHub for text-to-speech generation. This API, available at https://github.com/pedroetb/tts-api, created by Pedro Trujillo (GitHub username: pedroetb), is just one of them. Trujillo refers to his API as a “Text-to-speech REST API for multiple TTS engines.” REST is an acronym for representational state transfer and refers to the REST architectural style, which is an API architectural style built on URLs and standard HTTP methods. It is designed to be stateless, meaning each request is processed independently without saving data between requests. This reduces server-side application state and allows for parallel processing. Additionally, the use of HTTP with JSON data formats makes REST appropriate for web-based applications and is easily supported by most programming languages (Kaleb et al. 2019). Text-to-speech is a technology that converts text into audio. This specific API can be used to generate audio with multiple text-to-speech engines and various sound effects. The converted text can then be listened to on a local audio device or downloaded. The API supports four text-to-speech engines: Google Speech, gTTS, Festival, and eSpeak. Google Speech is a simple, multiplatform command-line tool that converts text into spoken audio using the Google Translate Text-to-Speech API. gTTS refers to the Google Text-to-Speech (gTTS) engine, as well as a Python-based library and command-line interface that provides access to this API. Festival is a free, open-source, multilingual speech synthesis framework available across multiple platforms, offering both a black box text-to-speech system and a flexible architecture for speech synthesis research. eSpeak is a compact, open-source speech synthesis engine that supports English and other languages and is compatible with Linux and Windows (Trujillo 2024). To use the API, you need to install Docker. When Docker is installed, run the following command-line instruction.<br>

docker run --rm -d --name tts-api --device /dev/snd -p 3000:3000 pedroetb/tts-api

This Docker command starts the API and makes it accessible at http://localhost:3000. According to Trujillo (2024), you can also deploy it in a Docker Swarm. When running, the API listens for POST requests at http://localhost:3000. You can interact with it using your preferred REST client or through the built-in web form. The API supports both playing audio and downloading audio files; these can be utilised using different voice codes depending on your needs. To use the built-in form, open http://localhost:3000 in your web browser, fill in the required fields, and submit the form. The API will process your input and return the corresponding audio output. You can also send a POST request directly to http://localhost:3000 using the following structure: <br>
<br>
Headers: <br>

Content-Type: application/json<br>

Body: <br>

{<br>
"voice": "google_speech",<br>
"textToSpeech": "hello world",<br>
"language": "en",<br>
"speed": "1"<br>
}<br>

You can use the command-line tool curl to play the converted audio directly,<br>
curl http://localhost:3000 \<br>
-d '{ "voice": "google_speech", "textToSpeech": "hello world", "language": "en", "speed": "1" }' \<br>
-H 'Content-Type: application/json'<br>
<br>
and to download the audio as a file:<br>
curl http://localhost:3000 \<br>
-d '{ "voice": "gtts_file", "textToSpeech": "hello world", "language": "en", "speed": "1" }' \<br>
-H 'Content-Type: application/json' \<br>
-o 'output.mp3'<br>
<br>
This allows you to either listen to the generated speech immediately or save it for later use.
This text-to-speech API could be used for linguistic research on the output of various text-to-speech models, since it allows you to utilise four different TTS engines. The audio outputs can be compared and judged on linguistic parameters, such as basic comprehensibility, as well as speech style, perception, and reception. Additionally, it would be interesting to evaluate the computer-generated output from the engines against naturally produced speech from a person to see if people can tell the difference and if they prefer one over the other. The API would make this research process easier and more efficient, and it could be integrated with other digital tools to visualise the data and support further analysis.

## GitHub
GitHub is a cloud-based service and website. It plays an important role in facilitating collaboration by providing a platform that helps developers store, manage, and organise their code, while also offering tools to track and control changes over time. Two key aspects of GitHub are the version-control principle and the use of Git. Git is a local version control system (VCS) that lets developers save “snapshots” of their projects over time. It is designed for individual use, enabling developers to monitor and manage changes to their code locally and then push the code to the main project. By combining Git's capabilities with GitHub's web-based interface, researchers and developers can collaborate in real time and maintain a log of who has contributed and what has been amended. This way, all participants in the project can see the changes already made, reducing the risk of duplicate work, and it is efficient. Another major strength of GitHub is its support for community-driven work. It acts as a hub where contributors can review, improve, and build upon each other’s efforts. This facilitates interdisciplinary collaboration and innovation. And for the humanities, this collaborative environment supports tasks such as text analysis, digital archiving, and mapping. It provides these tools, which are great for project management, and allows for a clear overview of potential issues and documentation of what work has been done, while simplifying the management of complex research projects and making the project accessible to multiple contributors at once.<br>
Developers can choose to make their work public and open source on GitHub. Open source refers to software whose source code is freely available for anyone to use, examine, and change. Open-source tools are a nice way to encourage knowledge sharing, since researchers can take the source code of the existing software and adapt it to fit their specific needs. It is also a way to test whether your research results are reproducible by allowing others to do similar research. By publishing their work on GitHub, researchers and developers can gain recognition while promoting the reality and value of shared authorship and the importance of sharing ideas and knowledge, which are essential aspects of academia. GitHub’s integration with various platforms and interfaces, such as APIs, and its support for multiple programming languages further enhance accessibility and encourage interdisciplinary projects.<br>

## Conclusion
GitHub offers a powerful platform for collaboration, allowing users to work together efficiently and transparently. Supporting community-driven, open-source projects, it facilitates knowledge sharing, reproducibility, and interdisciplinary study, making it a useful tool for modern research and academic collaboration. A practical example of this in research is the text-to-speech API developed by Pedro Trujillo (2024), which, as an open-source, GitHub-hosted resource, can be utilised in academic research to create new knowledge and share it with others. 

## References
Kaleb, K. et al. (2019). Expanding the Orthologous Matrix (OMA) programmatic interfaces: REST API and the OmaDB packages for R and Python. *F1000 research*. 842.<br>
Smuts, S. (2025). ‘Lecture 6: Open Source and Github Desktop’, *Digital Technologies in the Humanities*. Aarhus University. 20/10.<br>
Tarkowska, A. et al. (2018). Eleven quick tips to build a usable REST API for life sciences. *PLoS computational biology*. 14 (12).<br>
Trujillo, P. (2024) *TTS-API*. GitHub. Available at: https://github.com/pedroetb/tts-api (Accessed: December 16).<br>