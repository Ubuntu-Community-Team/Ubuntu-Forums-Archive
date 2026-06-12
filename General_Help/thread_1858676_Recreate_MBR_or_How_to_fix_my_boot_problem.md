---
title: "Recreate MBR? or How to fix my boot problem?"
date: 2011-10-12
forum: General Help
---

### Post by coolmate on 2011-10-12
Hi All,

First thing first, I make my situation clear.

I have a server, which was running ubuntu 8.04 on its interal HDs. Then, we added an external HD array (DELL PowerVault 1000) and installed ubuntu 10.04 on it. By some reason, the installation put boot loader (or mbr) onto the existing internal HDs. It was fine, we can run 10.04 from external HDs. 

Now the problems, we have to remove the old internal HDs. After removing (or disabling) them, we can not see or boot anymore. My guess is that the MBR is created on the previously-existing internal HD. 

So, how can I rebuild a new MBR on this new external HDs? Reinstall the whole Ubuntu 10.04 is not any option cause we have a lot data and other applications things on the server...

I've searched a lot articles. And just got myself lost. Cause none of them looks fine to my problem.

Any suggestion? Thanks in advance.

---

### Post by WorMzy on 2011-10-12
What do you mean by "the MBR is created"? I doubt that you mean a new MBR partition table is created, or else your entire post would probably be in caps-lock. However, you don't mention WIndows at all in your post, so I don't think that you mean that NTLDR is written to the boot sector either.

Some clarification is needed, in my opinion.

It would help if you could run this script: [http://sourceforge.net/projects/bootinfoscript/]("http://sourceforge.net/projects/bootinfoscript/") and post the results here, in code tags, preferably.

---

### Post by prodigy_ on 2011-10-12
> **WorMzy said:**
> What do you mean by "the MBR is created"?
Most probably he means Grub. Which, quite possibly, was on the internal HDD. And if that's the case, the solution is to reinstall Grub using a live medium. :)
[https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)

---

### Post by coolmate on 2011-10-12
Yes. It could be the GRUB. Actually I couldn't remember the exact words for it. Just remember there was a dialog during installation to let you choose which disk you want to put the thing on. I remember I clicked the default (or the first disk). That's what I think matters.

Better description? Sounds more like the grub thing? Thank you for your replies.

---

### Post by prodigy_ on 2011-10-12
Yeah. Boot from a LiveCD and reinstall Grub.

---

### Post by bishop__ on 2011-10-12
Your hunch is correct. Your MBR is looking for your old HD where grub was originally installed. 

To correct this, follow prodigy_'s advise and do the following:
1. mount your new HD that has the ubuntu 10.04
2. chroot to your newly mounted location
3. install grub from there. 
4. check grub.cfg (or grub configuration file) and modify them if necessary.
5. check /etc/fstab and modify them if necessary. 
6. reboot and test. 

Goodluck! ;)

---

### Post by coolmate on 2011-10-13
> **bishop__ said:**
> Your hunch is correct. Your MBR is looking for your old HD where grub was originally installed. 

To correct this, follow prodigy_'s advise and do the following:
1. mount your new HD that has the ubuntu 10.04
2. chroot to your newly mounted location
3. install grub from there. 
4. check grub.cfg (or grub configuration file) and modify them if necessary.
5. check /etc/fstab and modify them if necessary. 
6. reboot and test. 

Goodluck! ;)
Thanks. I am actually repairing the grub using boot-repair at this moment. Will report the result once it's done.

---

### Post by coolmate on 2011-10-14
Update:

haven't got the grub recovered. My server was installed with Ubuntu 10.04.3 LTS server edition which doesn't have the LIVE CD. I used desktop version of 64bits Ubuntu CD with Live Ubuntu. 

Used boot-repair, all fine until the last. It says please add a repository to your software Sources for [grub-pc] package. I tried some options and they don't work. I guess it requires the original server version 64 bit Ubuntu. I inserted the CD, it won't able to start the synaptic software manager.... Don't know what to do now...

---

