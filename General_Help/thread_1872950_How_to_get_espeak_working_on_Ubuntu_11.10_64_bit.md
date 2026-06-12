---
title: "How to get espeak working on Ubuntu 11.10 64 bit"
date: 2011-10-31
forum: General Help
---

### Post by xtracool_protik on 2011-10-31
I'm trying read it loud feature of acrobat, so need a text synthesizer, I've installed espeak and libgnome-speech libraries (it didn't work for acrobat right out of the box) so when I started espeak-gui through command line it gave me segmentation fault next I tried only espeak and here is output:
```

    ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib audio/pcm_bluetooth.c:1613:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1613:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1613:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1613:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started

```
Any ideas? or any alternative solutions for read it loud?

Thanks

---

### Post by WasMeHere on 2011-10-31
Hi xtracool_protik,

I'm using espeak, So maybe I can help you. Does it work when you run espeak from a command line with a little text string?

Have fun finding out about Ubuntu :-)
Olle

---

### Post by xtracool_protik on 2011-10-31
Yup it worked but still same errors..

---

### Post by WasMeHere on 2011-10-31
As long as it continues working, you can send the error output to the cyberspace with redirection of the error output **2>**
```
espeak -v en 'hello world' 2> /dev/null
```

In the manual, you find the options for loudness, pitch and speed, language (voices) etc. ```
man espeak
```

---

### Post by xtracool_protik on 2011-10-31
yea that would get rid of errors but still I can't use this one for read out loud feature of acrobat as I can't see acrobat detecting any speech synthesizer.

---

### Post by WasMeHere on 2011-10-31
Try ***pdftotext*** that can be installed from the repositories. It is in the "poppler-utils" (main). It works if the pdf was created so that the text flow is in sequence.
```
pdftotext filename.pdf - | espeak
```

---

### Post by xtracool_protik on 2011-10-31
Awesome that worked for 1 of the pdfs but not on 2 others, still didn't try on very big pdf file though. I'll continue using it till I find proper solution. Thanks :)

I had blogged about acrobat reader in past [http://hailubuntu.blogspot.com/2010/08/acrobat-read-out-loud.html](http://hailubuntu.blogspot.com/2010/08/acrobat-read-out-loud.html) I tried exact same procedure and it didn't work :-/

I've even tried orca but not sure how orca works (I guess its only for html / text)

---

### Post by WasMeHere on 2011-10-31
I'm glad it works for you at least partially.

Of course, if the pdf file is basically a picture (for example a scanned text), pdftotext can't do anything, and as I mentioned earlier, if the text is made up of blocks without following the text flow, the output will be garbled.

By the way, scanned text might be readable via OCR, but I have not used any tool for that (yet).

Good luck finding what you need :-)
Olle

---

### Post by Herbon on 2011-12-14
Bump

---

