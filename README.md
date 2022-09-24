
# whisper_streaming

[![CI](https://github.com/shirayu/whisper_streaming/actions/workflows/ci.yml/badge.svg)](https://github.com/shirayu/whisper_streaming/actions/workflows/ci.yml)
[![CodeQL](https://github.com/shirayu/whisper_streaming/actions/workflows/codeql-analysis.yml/badge.svg)](https://github.com/shirayu/whisper_streaming/actions/workflows/codeql-analysis.yml)
[![Typos](https://github.com/shirayu/whisper_streaming/actions/workflows/typos.yml/badge.svg)](https://github.com/shirayu/whisper_streaming/actions/workflows/typos.yml)

Streaming transcriber with [whisper](https://github.com/openai/whisper).
Transcribing in real time, enough machine power is needed.

## Example

```bash
# Setup
git clone https://github.com/shirayu/whisper_streaming.git
cd whisper_streaming
poetry install --only main

# If you use GPU, install proper torch and torchaudio with "poetry run pip install -U"
# Example : torch for CUDA 11.6
poetry run pip install -U torch torchaudio --extra-index-url https://download.pytorch.org/whl/cu116

# Run in English
poetry run whisper_streaming --language en --model base -n 20
```

- ``--help`` shows full options
- ``--language`` sets the language to transcribe. The list of languages are shown with ``poetry run whisper_streaming -h``
- ``-t`` sets temperatures to decode. You can set several like (``-t 0.0 -t 0.1 -t 0.5``), but too many temperatures exhaust decoding time
- ``-n`` sets interval of parsing. Larger values can improve accuracy but consume more memory.
- ``--debug`` outputs logs for debug

## Tips

## PortAudio Error

If you get ``OSError: PortAudio library not found``: Install ``portaudio``

```bash
# Ubuntu
sudo apt-get install portaudio19-dev
```

## License

- [MIT License](LICENSE)
- Some codes are ported from the original whisper. Its license is also [MIT License](LICENSE.whisper)
