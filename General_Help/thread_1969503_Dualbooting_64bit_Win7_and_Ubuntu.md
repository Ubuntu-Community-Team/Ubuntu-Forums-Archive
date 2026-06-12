---
title: "Dualbooting 64bit Win7 and Ubuntu"
date: 2012-04-30
forum: General Help
---

### Post by tonkatsu89 on 2012-04-30
Hey all, I've been wanting to get back into Ubuntu. I'm getting the iso now and I'm gonna buy a blank DVD later today and get ready to set it up but can someone help me out with setting it up to dual boot with my windows 7? I never actually figured that out myself, I just did a clean install. Would installing Ubuntu on a blank partition of my harddrive work, or would that cause problems? Thank you in advance!

---

### Post by kc1di on 2012-04-30
There are several options but here a page that will give you the information you'll need - Cheers! 

[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

---

### Post by tonkatsu89 on 2012-04-30
> **kc1di said:**
> There are several options but here a page that will give you the information you'll need - Cheers! 

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Thanks very much. Seems simple enough. I can't really back up my data too much but I'm not too worried about that. I have a laptop (which is past warranty) and it came pre-installed with win7 so I don't have a disk BUT I don't think I need to worry about that. Worst comes to worst I will be Windows-less again which hardly matters. I almost never play any games any more so it's not gonna be the end of the world. I always did have issues with Wine...

I'm not gonna mark this thread as solved just yet. I'm gonna keep it open in case I have trouble installing. Cheers!

---

### Post by Ubun2to on 2012-04-30
When I first installed Ubuntu, I used a live DVD, and it allows me to boot Windows 7 or Ubuntu.
I used Wubi to get 12.04 (since the DVD ISO file wasn't online when I tried to download it).
Feel free to make a separate partition-I just let it do its thing, and it worked just fine.

---

### Post by tonkatsu89 on 2012-04-30
> **Ubun2to said:**
> When I first installed Ubuntu, I used a live DVD, and it allows me to boot Windows 7 or Ubuntu.
I used Wubi to get 12.04 (since the DVD ISO file wasn't online when I tried to download it).
Feel free to make a separate partition-I just let it do its thing, and it worked just fine.

Alright. I'm downloading the 12.04 iso right now. I'm not sure if it automatically sets up the menu but I don't think it does. Either way by tonight I'll be using Ubuntu. I just gotta get to the store and buy a blank DVD.

---

### Post by Miykel on 2012-04-30
G'Day;  I found if I got "easeuse partition manager" from 

[http://www.easeus.com/download.htm](http://www.easeus.com/download.htm)

Set up a dedicated partition for Ubuntu  (ext4) plus a small partition for a swap, then install Ubuntu onto the partition and grub will allow you to boot into Ubuntu or W7
Hope this is of some help
Regards Miykel

---

### Post by zdeuyo on 2012-04-30
> **tonkatsu89 said:**
> Hey all, I've been wanting to get back into Ubuntu. I'm getting the iso now and I'm gonna buy a blank DVD later today and get ready to set it up but can someone help me out with setting it up to dual boot with my windows 7? I never actually figured that out myself, I just did a clean install. Would installing Ubuntu on a blank partition of my harddrive work, or would that cause problems? Thank you in advance!

Hello,


Also one thing to keep in mind since this seems to be happening a lot on this release of 12.04. If you cannot boot into Ubuntu and or into Windows, please follow the instructions on this thread so you can have both working.

Link: [https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

Please let us know if you have any questions.

All the best.

---

### Post by tonkatsu89 on 2012-04-30
> **Miykel said:**
> G'Day;  I found if I got &quot;easeuse partition manager&quot; from 

[http://www.easeus.com/download.htm](http://www.easeus.com/download.htm)

Set up a dedicated partition for Ubuntu  (ext4) plus a small partition for a swap, then install Ubuntu onto the partition and grub will allow you to boot into Ubuntu or W7
Hope this is of some help
Regards Miykel

 Yea I actually have easeus, so I may just do that.  > **zdeuyo said:**
> Hello,


Also one thing to keep in mind since this seems to be happening a lot on this release of 12.04. If you cannot boot into Ubuntu and or into Windows, please follow the instructions on this thread so you can have both working.

Link: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Please let us know if you have any questions.

All the best.

 Yea I read about that, thanks for the heads up.  Actually though I am having a problem that isn't entirely Ubuntu related. Twice I've supposedly burned the iso to disc but the disc is still blank, apparently. Something is going wrong. Anyone have any ideas? I tried once with imgburn and once with windows image burner or whatever it's called.

---

