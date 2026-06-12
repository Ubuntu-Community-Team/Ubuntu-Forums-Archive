---
title: "Windows CHKdisk has cocked up my wubi"
date: 2012-07-18
forum: General Help
---

### Post by Gusss on 2012-07-18
I have a dual boot system. Windows7 did a painfully long chkdisk  this morning in which it claimed to be recovering many files and "fixing" things. Now it seems to have done something to ubuntu. When I try an login I get :
> 
"[ Minimal BASH-Like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename. ]"

the found000 folder has 1 file called file0000.chk 1kb in size and a folder called dir0000.chk with a 1kb avg file in it.
Any ideas ?

---

### Post by JC Cheloven on 2012-07-18
> **Gusss said:**
> I have a dual boot system. Windows7 did a painfully long chkdisk  this morning (...)

As for the title of your thread, you don't really have a dual boot setup, but a wubi install of Ubuntu, which is a sort of fake install inside windows. 

This way, the whole install of ubuntu "lives" in a big windows file. On one hand, big files are more prone to internal errors. On the other hand, that big file is at the mercy of whatever windows wants to do with it. A windows file after all. If windows thinks the file has errors, tried to repair them, and failed, there is probably no much we can do. Perhaps trying to further repair from within windows using some other methods.

As you see, I'm not very enthusiastic with wubi installs. They can serve for trying out ubuntu, but they're not comparable to a true install (in dual boot for example).

Best
JC

---

### Post by Gusss on 2012-07-18
:icon_frown:

---

### Post by Nixarter on 2012-07-18
Never, ever run chkdisk :p  Chalk it up as a lesson learned, and disable it from auto-running at startup.  After some updates, it can actually re-enable itself, so always check.  I've seen many hard drives become corrupt from that program, and it completely removes headers, so the files are a pain to get back.

You may be able to salvage the virtual drive itself by backing it up and mounting it, but you're going to have to re-install ubuntu on that system.  I've spent weeks before trying to repair the damage done to the boot structure and files, but eventually gave up.

---

### Post by oldfred on 2012-07-18
Is root.disk still in your system as that is the wubi file. It may have just moved some of the support files that help it boot wubi from Windows. If so it may be easiest to backup root.disk, do a new install and replace the new root.disk with your old one. 

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)
how to fix those Wubi installation breakages without going crazy Rubi1200 Dec 2010
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)


If you are to the point of liking Ubuntu, then it may be time to convert to a full partitioned dual boot. From the creator of wubi:

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

---

### Post by JC Cheloven on 2012-07-18
> **Gusss said:**
> :icon_frown:

I'm really sorry. I encourage you to do a "real" install. It's the right thing to do for a production linux system. These tips should keep you safe:

1.- Resize (shrink) the windows partiton from within windows to make room for your ubuntu install. Leave the space unformatted.
2.- Install ubuntu to that free space, from live session or alternate install disk (safer).

Best 
JC

---

### Post by Gusss on 2012-07-19
Hi guys  - I guess Ill try a few windows things and then if not do a proper partition. The problem is I spent a couple of hours configuring a very tricky program with a specialist over skype and all that will be lost. ho hum - root is still there but only 0 kb ?

---

### Post by Gusss on 2012-07-19
> **oldfred said:**
> 

If you are to the point of liking Ubuntu, then it may be time to convert to a full partitioned dual boot. From the creator of wubi:


I love it -  I think its because I enjoy problem solving ;)

---

