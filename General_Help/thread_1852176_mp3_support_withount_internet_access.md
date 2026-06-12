---
title: "mp3 support withount internet access"
date: 2011-09-29
forum: General Help
---

### Post by adhamj90 on 2011-09-29
hello
I searched around and couldn't find a sure solution.
I have a computer on work. but i dont have any internet access there. i want to know if it is possibile to get the .mp3 and .avi support without internet.
i Have ubuntu on my laptop can i just copy some files from here and put them in the other computer at work after installing ubuntu?
I just want to be sure i could do it before i delete windows from the other one.

Thanks a lot in advance.

---

### Post by ajgreeny on 2011-09-29
Yes you can.

On the machine with internet access, fully update and add all the packages you need for mp3s (all the gstrteamer plugins, ubuntu-restricted-extras, w32codecs, etc etc) and then copy all the .deb files in /var/cache/apt/archives from that computer to the non-internet connected machine; into the same folder, of course, using a USB flash drive.
```
cp /var/cache/apt/archives/*.deb /media/*flashdrive*/
```Now on the other machine ```
sudo cp /media/*flashdrive*/*.deb /var/cache/apt/archives/
```Now you can update and add all those same packages without a problem and will not need the web as all packages will already be in the cache.

This will only work on the same OS version, but not if one is 10.04 and the other 11.04, for example.

---

### Post by fixerdave on 2011-09-29
There is also 'aptoncd' which you can install on an internet-enabled system and use it to build a CD that has all the packages you're interested in.  I haven't used it since 8.10 or so... but it worked well then.

---

