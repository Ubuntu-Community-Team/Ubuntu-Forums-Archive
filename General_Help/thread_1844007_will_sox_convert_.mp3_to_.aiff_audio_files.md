---
title: "will sox convert .mp3 to .aiff audio files?"
date: 2011-09-14
forum: General Help
---

### Post by ejames82 on 2011-09-14
hello,

in all fairness, I am also posting this question on at least one other popular linux forum.  I hope nobody takes offense.

I need to convert some music files from .mp3 to .aiff, but when I tried to use sox to do the conversion, I received the following message:

root@ed-desktop:/home/ed/audio cd2# sox *.mp3 *.aiff
sox FAIL formats: no handler for file extension `mp3'

Is there something that I am doing wrong?  I have read that sox would do this conversion.  Any help would be most appreciated.  :)

---

### Post by nothingspecial on 2011-09-14
Remove the sox you already have then do this

[http://ubuntuforums.org/showpost.php?p=9859875&postcount=8](http://ubuntuforums.org/showpost.php?p=9859875&postcount=8)

---

### Post by ejames82 on 2011-09-15
nothingspecial,

thank you so much.  your advise worked like a charm.  :)

---

### Post by andrew.46 on 2011-10-02
Helpful post that one :). I am not sure which version of Ubuntu it has occurred in (perhaps Natty??) but I believe more recent versions of Ubuntu can now get mp3 encoding with sox, easiest way is perhaps by adding the libsox-fmt-all package:

```
sudo apt-get install sox libsox-fmt-all
```

The Natty [changelogs]("http://changelogs.ubuntu.com/changelogs/pool/universe/s/sox/sox_14.3.1-2ubuntu1/changelog") seem to support this change although I am not entirely sure why this change of heart happened:

```

sox (14.3.1-2ubuntu1) natty; urgency=low

  * Merge from Debian unstable. Remaining changes:
    - Enable lame support (drop --without-lame and add libmp3lame-dev to
      build dependencies).

 -- Benjamin Drung <bdrung@ubuntu.com>  Sat, 12 Feb 2011 12:14:56 +0100

```

But it certainly makes life a little easier for all :).

---

