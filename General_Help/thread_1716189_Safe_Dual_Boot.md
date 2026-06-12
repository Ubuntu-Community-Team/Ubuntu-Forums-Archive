---
title: "Safe Dual Boot"
date: 2011-03-28
forum: General Help
---

### Post by anakynblade on 2011-03-28
Hi to all and befor I  begine I would like to say that I tried to use the search function befor posting and that I tried to understand as much as I could about dual booting befor tryng to start this post. And if I dident't find the corect ones I would kindly ask the moderators to move this post to a corect section.

Well here gous :).

I had on my PC a dual boot xp and Ubuntu perfect 10.10 I loved it very much :D but I had to reinstall win xp

when I first installed them It was xp installed and after I added Ubuntu ( note the first time I didn&#8217;tad a separate partition for Ubuntu so the ntfs was shrunken sow Ubuntu would fit).

After the installation everything was fine I had the boot menu I could chose whatever I wanted to use.

But it happen I didn&#8217;t paid enough attention to whine I installed and it messed up some thing in my xp. Sow I starter to reinstall xp my machine was like this C: D: E: 
C &#8211; win D- hdd files E:-Ubuntu I didn&#8217;t even delete the C: I just formatted it.

Everything ok win xp sp 3 works fine now the problem is that I can't seem to boot Ubuntu.

I have done some reading and I understand that I busted up the Grub. I don't want to recover anything bechouse it is not very important , but I will use this PC for work and in the future it will be nasty to have such a problem ,

My question is How can I create my partitions sow that just in case I will bust up one of them reinstalling doesn&#8217;t mean loosing the other one for instance if I reinstal xpUbuntu will still boot and the other way around.

Sorry for the long description I tried to be very explicit and hope that some one can help me figure this out.

I toght like this :
-format all hdd 
-allocate 3 partitions 
-c d and e 
-c xp d hdd and e ubuntu
-install first xp then add on ubuntu .
But frankly except the part when I create different partitions from the start , I did the same steps the last time and got busted .

Thanx in advance for any reply that is related to this topic.
Sorry for my english.

---

### Post by ridgeland on 2011-03-30
I like to use multiple 10GB partitions for Ubuntu and much more for a Data partition.  

On my wife's laptop we have Windows. I set it up with Windows 20GB, swap 2GB, Linux 8GB, Linux 8GB, Linux 8GB, Data 12GB. I have multiple versions of Linux on it.  Two copies of 10.10 and a LAMP 10.10.  "Dual boot" can boot a list of partitions, not just 2.

For a helper CD I keep SystemRescueCD around.
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)
It's good for Grub repair work or partitioning etc.

Why not share your location with us?  To me part of the fun of forums like this is the big big world.

---

### Post by oldfred on 2011-03-31
Welcome to the forums.

You mention c:, d: etc, those are Windows. Ubuntu uses sda1, sda2 etc. So did you install wubi into e:?

Do you have an Ubuntu liveCD. If so post this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

