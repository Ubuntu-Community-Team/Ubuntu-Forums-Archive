---
title: "can't boot ubuntu after installing updates"
date: 2010-12-03
forum: General Help
---

### Post by NorthernArcher on 2010-12-03
I am running a dual boot system - Ubuntu / Win. XP

I installed the security updates in Ubuntu and followed the prompt to restart the computer.  Now I can't boot into Ubuntu.  When I try, the machine simply restarts.  I can still log into windows just fine, but Ubuntu won't load no matter how many times I try.

Any help would be greatly appreciated, as I dislike using Windows and would like to return to Ubuntu as soon as possible.

Thanks,

Jason

---

### Post by subtroniq on 2010-12-05
The same issue here.My ubuntu 10.04 is installed in Vista.Ubuntu prompt me to update, restart and now stucked - no chance to log in.

---

### Post by Rubi1200 on 2010-12-05
Hi and welcome to the forums NorthernArcher and subtroniq :)

If you are both able to boot into Windows normally, but the problem is Ubuntu please confirm that this is a Wubi install.

---

### Post by subtroniq on 2010-12-05
confirmed

---

### Post by Rubi1200 on 2010-12-05
Hi subtroniq,
thanks for the confirmation :)

Now let's see if we can get this sorted out for you.

There are updates to the GRUB program at the moment which are causing problems with Wubi installs.

The following link describes some of the issues and the fixes:
[http://ubuntuforums.org/showpost.php?p=10159040&postcount=5](http://ubuntuforums.org/showpost.php?p=10159040&postcount=5)
(use the partition number appropriate for your setup)

This link shows you how to avoid the problem for the foreseeable future:
[http://ubuntuforums.org/showpost.php?p=10180520&postcount=78](http://ubuntuforums.org/showpost.php?p=10180520&postcount=78)

Good luck and let me know how it goes please.

---

### Post by subtroniq on 2010-12-05
Thank you very much, Rubi1200!
I`ll read and try to fix.
The results will be posted by me as soon as i can.

---

### Post by subtroniq on 2010-12-07
I was not able to fix my problem.It is too difficult for me to understand what this people was doing.

"If it's a 10.04 install, the fix is to boot an Ubuntu live cd, loop mount the wubi root.disk and manually edit the grub.cfg."

LIVE CD??
LOOP MOUNT??

They have totally lost me:P.I will reinstall on a separate partition and will never ever use wubi install again.I will consider wubi as the "trial" version of Ubuntu.:P

Thank you for trying to help me!

---

### Post by Rubi1200 on 2010-12-07
> **subtroniq said:**
> I was not able to fix my problem.It is too difficult for me to understand what this people was doing.

"If it's a 10.04 install, the fix is to boot an Ubuntu live cd, loop mount the wubi root.disk and manually edit the grub.cfg."

LIVE CD??
LOOP MOUNT??

They have totally lost me:P.I will reinstall on a separate partition and will never ever use wubi install again.I will consider wubi as the "trial" version of Ubuntu.:P

Thank you for trying to help me!

Are you sure? I can walk you through it step by step if you want.

To be honest, installing to the hard-drive is a better option.

You are more than welcome too :)

---

### Post by subtroniq on 2010-12-12
Ok, Rubi1200 - i`m ready to try the "step by step" way.It`s pity to give up easy, when i got you on my side:D.What is next?

---

### Post by Rubi1200 on 2010-12-12
Glad to hear it!

Okay, since you last posted some things have changed that will hopefully make this easier for you.

Read the information in this thread and then come back here if you still have questions about what to do and I will walk you through it.
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by subtroniq on 2010-12-14
success!! i can access and backup my data now!;).

Thanks once again, Rubi1200! 

It is never too late to learn:D (how to get rid of wind**OS**)

---

### Post by Rubi1200 on 2010-12-14
> **subtroniq said:**
> success!! i can access and backup my data now!;).

Thanks once again, Rubi1200! 

It is never too late to learn:D (how to get rid of wind**OS**)

You are more than welcome :D

Glad you got it sorted out.

---

