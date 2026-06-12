---
title: "run multiple instances of ushare ubuntu"
date: 2010-11-22
forum: General Help
---

### Post by Gh3ttoman on 2010-11-22
I have multiple hard drives with videos on them and i can only get the my xbox to read the 1st in my list of directories. So i wanted to know can i run multiple instances of ushare and use one for each hard drive? Is it possible?

---

### Post by Pollox on 2010-11-22
This seems to be a bug with ushare ([http://sourceforge.net/tracker/?func=detail&aid=1847112&group_id=151880&atid=782408](http://sourceforge.net/tracker/?func=detail&aid=1847112&group_id=151880&atid=782408)). I'm not sure if anyone is developing it still or if that sourceforge site is even the latest code for it (but I think it is). So I don't have much hope of it being fixed anytime soon.

You could try starting different instances reading form different config files, i.e.
```
ushare --cfg=configfile
```
Be sure to set different numbers in the USHARE_PORT option of different config files.

---

### Post by Gh3ttoman on 2010-11-22
Ok. Will try this today.

also the page you showed me: [http://sourceforge.net/tracker/?func=detail&aid=1847112&group_id=151880&atid=782408](http://sourceforge.net/tracker/?func=detail&aid=1847112&group_id=151880&atid=782408)

the lone comment on the page has a fix: I'm having this problem as well. The way I fixed it was to do a mount
--bind of the additional folders into folders within the original.

so ill try this too.

you know what, i didnt even do any of these. All i did was change the mount points for all my hard drives to point to different folders inside the same folder. then i just used that folder as the ushare directory, and Bam all the folders with the mounted hard drives pop up. i cant believe it was that simple. thanks anyway.

---

### Post by priegog on 2010-12-31
Ah, I wanted a fix for this, but for a different reason. (I want one for videos and stuff, and another for music while gaming, because if I add everything to the same, it'll try to grab the videos as music). 

Did you learn anything useful on how to achieve multiple instances?

---

