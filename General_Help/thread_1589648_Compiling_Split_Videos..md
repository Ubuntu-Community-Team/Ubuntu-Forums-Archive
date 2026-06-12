---
title: "Compiling Split Videos."
date: 2010-10-06
forum: General Help
---

### Post by DeathByLinux on 2010-10-06
Hey guys,
              I needed some help with this problem, which may end up taking seconds of your time. I downloaded a video that was 400ish megs, and the guy who uploaded them split it into two files, one of which is an easy to play .mwv file and the other is a ".crc" file. I am not sure how he split them, but I am guessing that he used a program called HJSplit, but I am not %100 sure about that. 
Any ideas?
-Thanks for reading.

---

### Post by Jahid65 on 2010-10-06
open synaptic & search "lxsplit"(without the quote). It may be called command-line version of hjsplit. It is used to split or join files.

Suppose the videos are in Desktop. Now open terminal & type:
```
cd ~Desktop
```
This will take you to the desktop folder. Suppose videos name are video.flv.001 to video.flv.004. Now run the following command:

```
lxsplit -j video.flv.001
```
 this will join 4 parts into one. 

 you can also use hjsplit or peazip to do the same job. both have linux version.

---

### Post by DeathByLinux on 2010-10-06
> **Jahid65 said:**
> open synaptic & search "lxsplit"(without the quote). It may be called command-line version of hjsplit. It is used to split or join files.

Suppose the videos are in Desktop. Now open terminal & type:
```
cd ~Desktop
```This will take you to the desktop folder. Suppose videos name are video.flv.001 to video.flv.004. Now run the following command:

```
lxsplit -j video.flv.001
``` this will join 4 parts into one. 

 you can also use hjsplit or peazip to do the same job. both have linux version.

Thanks a lot, Jahid. 
I had a bit of trouble at first because I kept writing "cd ~Desktop" rather than simply "cd Desktop". Figured out my mistake then moved on to the next problem, which was that the .crc file was not the other half, so I got the other half and tried the instructions again, and it worked. :)
-Thanks for your time and consideration.
-DeathByLinux

---

### Post by maki_to13 on 2010-10-25
Hello! I've been having similar problems with joining files.

The files I want to join -are- in fact on the desktop, but when I type "cd Desktop" (tried it with and without tilde), it says "no such file or directory." Am I doing something wrong?

---

### Post by maki_to13 on 2010-10-25
((accidentally double posted. Can't seem to delete the post, so I will leave this here as my meek apology for being a complete n00b))

---

