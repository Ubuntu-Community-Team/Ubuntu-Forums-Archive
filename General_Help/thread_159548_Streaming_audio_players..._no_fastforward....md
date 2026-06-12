---
title: "Streaming audio players... no fastforward..."
date: 2006-04-13
forum: General Help
---

### Post by fonggiding on 2006-04-13
I am a big streaming audio listener, mostly wma, but am discontent with totem to play them. Problem one: no fast forward or rewind. Problem two: after I pause a stream and then replay it starts from the beginning. That is about it. In Window$ Media Player I remember being able to skip forward and back when playing streaming audio. Please help me.](*,)

---

### Post by doclivingston on 2006-04-13
The technical answer to this is that GStreamer isn't reporting the stream as seekable, because it doesn't know if it is or not.

As far as I know, there is no easy way to tell whether a stream is seekable (e.g pre-recorder) or non-seekable (e.g. live radio). If anyone does know a good method, I'm sure the GStreamer developers would be interested to hear it.

---

### Post by fonggiding on 2006-04-13
Hmmm. Sticky situation indeed. I am listening to pre-recorded bits of the Rush Limbaugh(yes. I know. He uses Mac...) program if that is of any help. Listening to the same stream in Window$ I was able to rewind and such, unless that doesn't matter. Thanks for the response I'll try to check more into this using my limited noob powers:confused: .

---

### Post by rabidphage on 2006-04-13
[QUOTE=fonggiding]Hmmm. Sticky situation indeed. I am listening to pre-recorded bits of the Rush Limbaugh(yes. I know. He uses Mac...) program if that is of any help. Listening to the same stream in Window$ I was able to rewind and such, unless that doesn't matter. Thanks for the response I'll try to check more into this using my limited noob powers:confused: .[/QUOTE]
There is a saying in my language (malayalam)
roughly translated it means something like
"and the baby squirrel did his worth"

a very good gesture from your part....:KS

---

