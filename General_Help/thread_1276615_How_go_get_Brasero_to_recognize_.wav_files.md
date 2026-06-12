---
title: "How go get Brasero to recognize .wav files?"
date: 2009-09-27
forum: General Help
---

### Post by 3pinner on 2009-09-27
Ubuntu 8.10
Gnome desktop
Lightscribe and some other (no name on the drawer) DVD/Cd burners.
I am trying to copy a Disk with .wav files to another disk.
Brasero does not recognize.wav files. Says disk is empty.

Any plug-ins available for this?
2oz framing hammer maybe??

Thanks

---

### Post by scouser73 on 2009-09-27
Have you considered using a program like Sound Converter to make the .wav files into .mp3 files?

Go to **Add/Remove** select **All Available Applications** from the drop-down menu and then scroll to find **Sound Converter** and install.

---

### Post by davegunnoe on 2010-06-06
Bump.

I just installed 10.04 and all my .wav files are 0 bytes and won't play. I had Ubuntu Studio 9.04 installed before this and the .wav files were fine. 

I've tried using the converter suggestion but it won't recognize them either. I've installed ubuntu-restricted-extras and gstreamer-ugly codecs, but nothing seems to fix the problem. Strange.

Any help is appreciated. Thx

---

### Post by 3pinner on 2010-06-06
Hello,
I posted this thread originally, and I also just installed Lucid Lynx.
My .wav files are recognized and played by Movie Player.

But I gave up on Brasero and loaded K3B from the repositories. Much easier to work with and it recognizes and works with .wav and every other audio file I need to work with.

go to Applications> Ubuntu Software Center and type K3B in the search box in the upper right hand corner. click on the icon for K3B, click Install. It wil ask for your password, enter that and follow the prompts.
Please post back with how things turn out.

---

### Post by davegunnoe on 2010-06-06
Thanks for the quick reply.

I've used K3B for quite a while, but I just decided to switch to brasero because it was packaged with Ubuntu and it has pretty much always done what I've needed it to do (mostly burning iso files and ogg cd's). Although K3B is still my first choice if I need to do something more complicated) 

I chose this thread because it seemed to relate to my issue enough to not warrant another thread. My issue is (was) .wav files not being playable system wide. I thought the problem was with not having the correct codec however I believe I've figured it out.

I have .wav support, because I was able to convert other files into .wav files and play them perfectly. The fact that I can convert to .wav tells me that I have the codec necessary to handle the file type and therefore my files must be the problem (I guess they were corrupted somehow). If this logic is flawed let me know. But I think this is the case.

I only had a hand full of wav files anyway. I'll just ditch them any buy some new ogg's. Frankly I'm ashamed to have wav files on my PC anyway. lol

Thanks alot!

---

