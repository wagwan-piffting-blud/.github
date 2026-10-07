# Howdy, I'm Wags.

I make things on the Internet for fun, and break stuff sometimes. It's super entertaining! Most of what I build lives in the overlap between **emergency alerting**, **speech synthesis**, and **dragging old tech back from the dead before it disappears for good**.

Lately (as of 2026-10-07), that mostly means taking a discontinued TTS engine apart and putting it back together in Rust or C, **sample-for-sample identical** to the original, so it can run anywhere without the DLL it came from. This includes Windows, Mac, and Linux (down to a Pi Zero) builds, and even WebAssembly for the browser for builds that warrant it. I also do a lot of work with EAS/SAME and NOAA Weather Radio, including decoding, encoding, and (rarely) generating mock alerts.

If you came here looking for some (quite old) puzzles instead, I host those (and training for them) over at [wagspuzzle.space](https://wagspuzzle.space/). There's some other odds and ends on the site too!

---

## A short statement on Generative AI and its use in my (publicly facing) work

I frequently collaborate with Claude/Claude Code on most things nowadays. Like most things in life, it is a **tool**, a means to an end, nothing more. It's not a companion, nor sentient (at least, yet!), but it is _extremely_ helpful for code generation, reverse engineering, and (sometimes) documentation. I mostly use it for the code-facing "grunt work" parts of my projects, and for brainstorming ideas/working out problems. However, I do not use it for art or as a replacement for human creativity, or for any work that is meant to be original or creative in nature. If you do wish to see the parts of my work that were generated with AI assistance, I will happily point them out to you, and I will always be transparent about it. Each repository used with AI assistance will be clearly marked at the bottom of the README in a heading, disclosing which models/providers were used and that AI was used overall. If you have any issues or questions about my use of AI, please feel free to reach out to me via email or Discord. I am always happy to discuss my work and my use of AI in it, and my thoughts in more depth than a simple README blurb can convey.

---

## 📡 Emergency Alerting + Weather Radio

Encoding, decoding, and understanding EAS / SAME and NOAA Weather Radio.

- **[EAS-Tools](https://github.com/wagwan-piffting-blud/EAS-Tools)** -- a fully client-side EAS/SAME toolkit: decoder, encoder, text crawl generator, audio splicer, and more. Lives at **[eas.tools](https://eas.tools/)**, and is on [Google Play](https://play.google.com/store/apps/details?id=com.wagspuzzle.eastools) and the [App Store](https://apps.apple.com/us/app/eas-tools/id6759717275). My most-used project.
    - **[seatty-same-wasm](https://github.com/wagwan-piffting-blud/seatty-same-wasm)** -- the SeaTTY 2.65 SAME demodulator, reverse-engineered and ported to Rust/WASM SIMD. Bit-identical to the JS reference and 7-8x faster; it powers the EAS-Tools decoder.
    - **[EAS-Tools-Audacity-WASM](https://github.com/wagwan-piffting-blud/EAS-Tools-Audacity-WASM)** -- a 32-bit x86 interpreter + JIT, PE loader, and VST2/LADSPA host in C, compiled to WASM. Runs unmodified Windows plugin DLLs in the browser so EAS-Tools can render all 582 Audacity 2.4.2 macros, faster than native Audacity.
- **[EAS_Listener](https://github.com/wagwan-piffting-blud/EAS_Listener)** -- a Rust-native software ENDEC. Monitors broadcast streams, decodes and records alerts, pushes notifications via Apprise, relays to Icecast, and has a live dashboard. Ships as a Docker image with five TTS engines to pick from.
- **[E2T-NG](https://github.com/wagwan-piffting-blud/E2T-NG)** -- EAS2Text, Next Generation. Turns a raw SAME header into plain English, with ENDEC emulation modes (SAGE, TFT, Trilithic, DASDEC, and more), in JavaScript, Python, and Rust.
- **[EMNet_Mocker](https://github.com/wagwan-piffting-blud/EMNet_Mocker)** -- mock EAS alerts spliced from ComLabs EMNet voice files.
- **[OpenCRS](https://github.com/wagwan-piffting-blud/OpenCRS)** -- a preserved reupload of datajake1999's CRS-style NWS forecast generator, after the original went 404.

## 🗣️ Speech Synthesis + Voice Preservation

Recovering discontinued/mostly proprietary TTS voices and wiring them into things that talk again on any computer from the last 20 or so years.

**Native engine re-implementations** (no original DLLs/EXEs, no Wine, no emulator, just pure code):

- **[dectalk-rs](https://github.com/wagwan-piffting-blud/dectalk-rs)** -- DECtalk 4.60, the NWS build used on NOAA Weather Radio, in pure Rust. Sample-for-sample identical to the original `dectalk.dll`, in one static binary for Windows, Linux (down to a Pi Zero), and macOS.
- **[Speechify](https://github.com/wagwan-piffting-blud/Speechify)** -- the 2003 Speechify 3 engine, rewritten in C as `spfy`. Byte-exact with Speechify 3.0.5, and the base for ongoing Speechify 2.1.5 reverse-engineering.
- **[vtns-rs](https://github.com/wagwan-piffting-blud/vtns-rs)** -- VoiceText / NeoSpeech (Paul, Kate, Julie, James, Violeta) in Rust, bit-identical to the original engine DLLs across the 2009-2014 builds.
- **[ENDEC_Dave](https://github.com/wagwan-piffting-blud/ENDEC_Dave)** -- the ubiquitous Loquendo Dave voice, liberated from a real DIGITAL ENDEC. Runs on Windows via SAPI, or natively anywhere through the `loqng` Rust crate.
- **[cep6-rs](https://github.com/wagwan-piffting-blud/cep6-rs)** -- a small, fast Rust engine for Cepstral 6 voice banks (bring your own voices).

**SAPI5 voices:**

- **[AcuVoice-Roger](https://github.com/wagwan-piffting-blud/AcuVoice-Roger)** -- the desktop "Roger" voice, once trialed as a NOAA Weather Radio voice, rescued from obscure children's software and repackaged for SAPI5 (see the archived [Fonix-Roger](https://github.com/wagwan-piffting-blud/Fonix-Roger) for the lineage).
- **[FonixJessicaSAPI](https://github.com/wagwan-piffting-blud/FonixJessicaSAPI)** -- the Fonix "Jessica" Pocket PC voice, running on the desktop FAAST engine with a reverse-engineered Cybit sound bank decoder. Same origin as Fonix-Roger, but a different voice.
- **[FestvoxKalMonotone](https://github.com/wagwan-piffting-blud/FestvoxKalMonotone)** -- mild poking at the Festival Speech Synthesis System.

## 🎮 Game Preservation

- **The Beat Revival** -- keeping *Mirror's Edge: Catalyst* (2016) UGC alive. More at [beatrevival.me](https://www.beatrevival.me/).

## 🧩 Odds + Ends

- **[CCIDB](https://github.com/wagwan-piffting-blud/ccidb)** -- the Coin Collection Information DataBase, an open-source coin collection tracker. NO LONGER UPDATED/MAINTAINED.
- **[project-skydrop](https://github.com/wagwan-piffting-blud/project-skydrop)** -- solver scripts for the [Project Skydrop](https://projectskydrop.com/) puzzle hunt. NO LONGER UPDATED/MAINTAINED.
- **[StreamDeckFolderEditor](https://github.com/wagwan-piffting-blud/StreamDeckFolderEditor)** -- moves the "back" button inside Stream Deck folders, after the BarRaider original stopped working for a time. NO LONGER UPDATED/MAINTAINED.

...and always with more to come.

---

## Tooling I usually reach for

`Rust` · `C` · `Python` · `JavaScript/HTML/CSS` · `WebAssembly` · `C++`

...plus Ghidra for the reverse-engineering half, and whatever a given project drags me into (Scheme, PHP, Kotlin/Swift, plain bash, you name it).

---

## 📊 The numbers

<p align="center">
  <img src="./profile/stats.svg" alt="Stats" />
  <img src="./profile/streak.svg" alt="Streak Stats" />
</p>

---

## 📫 Find me

- Website + contact form: **[wagspuzzle.space](https://wagspuzzle.space/)**
- Keybase (not really used much): [wags2piffting](https://keybase.io/wags2piffting/)
- Discord: `@wags2piffting` (DMs open, but please be patient if I don't respond immediately or see your DM due to the Discord filters)
- Plain email: `contact` ['ae t] `wagspuzzle` [d aa t] `space`

I check my emails and GitHub issues multiple times a day, and am always eager to chat, though **responses may be delayed depending on how busy I am at any given moment**. I am quite busy, especially with the number of repositories I maintain for others. Thanks for visiting my profile!
