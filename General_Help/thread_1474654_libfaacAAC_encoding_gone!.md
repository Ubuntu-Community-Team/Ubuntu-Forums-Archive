---
title: "libfaac/AAC encoding gone!"
date: 2010-05-06
forum: General Help
---

### Post by LanternInc on 2010-05-06
I used mencoder to convert videos to psp/mp4 with x264 and aac encoder. Since aac encoders were removed, are there any other audio encoders that will play in psp/mp4(newer versions of PSPs)? I'm trying libmp3lame from libavcodec's   audio codecs with no luck.

---

### Post by cdenley on 2010-05-06
```

echo "deb http://packages.medibuntu.org/ lucid free non-free" | sudo tee -a /etc/apt/sources.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
sudo apt-get install mencoder

```
[https://bugs.launchpad.net/ubuntu/+source/faac/+bug/374900](https://bugs.launchpad.net/ubuntu/+source/faac/+bug/374900)

---

### Post by LanternInc on 2010-05-06
[I]echo "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free" | sudo tee -a /etc/apt/sources.list
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
sudo apt-get install mencoder[/I]
I was able to encode a video with aac, but there were no video codec in the properties in the psp. I still can't play it in the psp. 

I'm using this:

mencoder -mc 0 -af volume=5:0 -subfont-text-scale 3 -vf pullup,softskip,dsize=480:272,\
scale=0:0,harddup,unsharp=l3x3:0.5 \
-ofps 24000/1001 -oac faac -faacopts br=128:mpeg=4: object=2:raw \
-channels 2 -srate 48000 -ovc x264 -x264encopts \
bitrate=500:global_header: partitions=all:trellis=1:level_idc=30:threads=2 \
-of lavf -lavfopts format=psp input.video -o output.video

---

### Post by cdenley on 2010-05-06
[http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-handheld-psp.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-handheld-psp.html)

---

### Post by LanternInc on 2010-05-06
[I][http://www.mplayerhq.hu/DOCS/HTML/en...dheld-psp.html]("http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-handheld-psp.html")

[/I]I searched this one already. It doesn't work. 

I tried PSPVC just now and it works. But mencoder with x264 + faac gives better video quality, less video file size and significantly faster than pspvc in encoding*. *I would still like to use mencoder.

--
*Sorry. I didn't know that the thread icon above is angry. I thought it was crying sad.*

---

### Post by cdenley on 2010-05-06
> **LanternInc said:**
> [I][http://www.mplayerhq.hu/DOCS/HTML/en...dheld-psp.html]("http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-handheld-psp.html")

[/I]I searched this one already. It doesn't work. 

I tried PSPVC just now and it works. But mencoder with x264 + faac gives better video quality, less video file size and significantly faster than pspvc in encoding*. *I would still like to use mencoder.

--
*Sorry. I didn't know that the thread icon above is angry. I thought it was crying sad.*

Well if the command suggested by the official documentation doesn't work for you, I certainly won't be able to give you a better one.

---

### Post by LanternInc on 2010-05-06
I tried a couple of videos with different containers: avi and mkv, they all work fine even with aac. But still not working with the psp. For now I guess.

 I'm gonna mark this as solved. The second post already answered the libfaac/aac question.
----
Thanks for the replies.

---

### Post by jotape99 on 2010-06-21
Did you find a solution for mencoder and x264 lib ?

---

### Post by Redsandro on 2010-07-02
> **cdenley said:**
> ```

echo "deb http://packages.medibuntu.org/ lucid free non-free" | sudo tee -a /etc/apt/sources.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
sudo apt-get install mencoder

```
[https://bugs.launchpad.net/ubuntu/+source/faac/+bug/374900](https://bugs.launchpad.net/ubuntu/+source/faac/+bug/374900)

Thanks. I was wondering where my AAC support went, but that fixed it.

---

