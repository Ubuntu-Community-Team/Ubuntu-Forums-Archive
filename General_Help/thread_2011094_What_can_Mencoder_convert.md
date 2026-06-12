---
title: "What can Mencoder convert?"
date: 2012-06-26
forum: General Help
---

### Post by hakermania on 2012-06-26
I like the quality that mencoder produces but it isn't quite clear to me what are the formats that it can handle!

In most of the examples that I've seen online, many persons use as input file an AVI file, but the output is still an AVI file, so they basically do cropping, they edit the audio of the input AVI file etc...

I am mostly interested in converting an input file to other formats. I've seen that mencoder can convert .mpg files to .avi files. But, what else?

Another thing that confuses me is that, if, for example, I give this:
```

mencoder "sample file.avi" -oac mp3lame -ovc lavc -o output.3gp

```
then mencoder normally generates the output.3gp file, and
```

vlc output.3gp

```
plays it very well, with very nice quality, just like I want it for my mobile phone... LIES!
The following:
```

file output.3gp

```
reports:
```

output.3gp: RIFF (little-endian) data, AVI, 256 x 240, >30 fps, video: FFMpeg MPEG-4

```
which makes me believe that the output.3gp file is still AVI.

What am I missing!?

Thanks in advance for any answers!

---

### Post by O2Blevel on 2012-06-26
I don't have much experience with mencoder but here's a good resource for it:

[http://www.mplayerhq.hu/DOCS/HTML/en/mencoder.html]("http://www.mplayerhq.hu/DOCS/HTML/en/mencoder.html")

---

