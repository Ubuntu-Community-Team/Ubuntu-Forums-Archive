---
title: "Audacious in Conky"
date: 2009-07-15
forum: General Help
---

### Post by pkjm17 on 2009-07-15
I currently have Audacious in Conky which displays the song name, time of song, and progress bar of the song, however, everytime I start a song the progress bar fills up right away. I thought it's supossed to go along while the song plays?

Here's what I have in Conky for it.

MUSIC ${hr 2}
${if_running audacious}${exec audtool --current-song}
${exec audtool --current-song-bitrate-kbps} kbps / ${exec audtool --current-song-length} ${execbar expr 100 \* $(audtool --current-song-output-length-seconds) \/ $(audtool --current-song-length-seconds)}$endif

---

### Post by ChillyCheeze on 2012-02-26
First off: Thanks a lot. I have tried making that bar, but didn't exactly get it to work.
I have no idea how i doesn't work for you, because what you posted(and i use now) works perfectly(for me)

---

### Post by tomski on 2012-03-24
thnx for this saved me some time & so i thought i would fix yours & save you some time

To get the progress bar to work use the following:
```

${execbar expr $(audtool --current-song-output-length-seconds) \* 100 / $(audtool --current-song-length-seconds)
```

looks like the logic was miss typed lol

---

