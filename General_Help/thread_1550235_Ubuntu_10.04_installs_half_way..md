---
title: "Ubuntu 10.04 installs half way."
date: 2010-08-10
forum: General Help
---

### Post by from_beyond on 2010-08-10
I tried several Ubuntu 10.4 Disks both bought and burned by myself. The problem is that the installation goes to about 42% then aborts. I get a message box telling me that "is often due to a faulty cd/dvd disk or drive or a faulty hard-disk".
I don't buy it. Just replaced my DVD drive and reformatted my hard disk with no errors. I also ran memtest86 with a passing score on my 2 GB of ram.
I also installed Debian Lenny with no problems:
[http://users.lmi.net/subjazz/images/debian.png](http://users.lmi.net/subjazz/images/debian.png)
I also installed Backtrack4 with no problems.

I believe my next hope is to bring this system to service because I ran out of options. To be Frank I like Debian Lenny but as a Desktop with bleeding edge goodies etc Ubuntu or Ubuntu Ultimate 2.7  is what I much prefer. I have several swap-out drives and would really like to install the latest Ubuntu--Thanks for any suggestions you may have.

UPDATE ON THIS PROBLEM:
I tried a text based installation of Alternative Ubuntu 10.04. It installed flawlessly so now I am pretty sure the problem all along was bad memory which needs to be replaced. Thanks to the individual that suggested it to me!

UPDATE AS OF September 24, 2010:
Nothing is wrong with my RAM. Tested using Memtest for 48 hours.
Have a new optical drive.
Formatted my hard disk with no bad sectors or errors.
All Bios SETTING ARE GOOD.
Ubuntu Live disks tested good on other systems.
Nothing wrong with my PC and Nothing wrong with disks.
I only have one option left and that is to disable temporarily, my hard drive in the BIOS.

---

### Post by MatthewAdams on 2010-08-10
When you try to install, have you tried going through the live desktop and doing it that way? Or do you try going straight to "install from this disk" or whatever that option is? 

I've always had a bit more luck going through the live desktop and then trying to install from there.

---

### Post by ezsit on 2010-08-10
Also, try the alternate disk. The alternate disks use a text-based installer and usually work best.

---

### Post by from_beyond on 2010-08-10
I tried to install direct and also from the Gnome. Both gave me similar results. I used several Disks so it's not a disk issue.
I suspect it may be my RAM and when I collect enough beer bottles I will replace them. I hear that memtest is not 100% accurate. noacpi is not something I tried but to me its a waste of time. I believe the issue is hardware related but funny how Debian and Backtrack had no problem with installation!
If it is my memory then Ubuntu should be smart enough to tell me that and not give me a faulty drive etc. pop-up notice. 
I been using Ubuntu for several years and now I'm hooked on it. I am a desktop person and like things the easy way for the most part. 
Debian Lenny is good for now but you really have to get into group permissions which sometimes can be a pain.
My next install will be the Ubuntu Ultimate 2.7. I am determined to get this installed one way or the other.

---

### Post by oleink on 2010-08-10
> **from_beyond said:**
> I tried to install direct and also from the Gnome. Both gave me similar results. I used several Disks so it's not a disk issue.
I suspect it may be my RAM and when I collect enough beer bottles I will replace them. I hear that memtest is not 100% accurate. noacpi is not something I tried but to me its a waste of time. I believe the issue is hardware related but funny how Debian and Backtrack had no problem with installation!
If it is my memory then Ubuntu should be smart enough to tell me that and not give me a faulty drive etc. pop-up notice. 
I been using Ubuntu for several years and now I'm hooked on it. I am a desktop person and like things the easy way for the most part. 
Debian Lenny is good for now but you really have to get into group permissions which sometimes can be a pain.
My next install will be the Ubuntu Ultimate 2.7. I am determined to get this installed one way or the other.

How much of your hard drive are you trying to take up

---

### Post by from_beyond on 2010-08-10
I tried a 750 GB IDE drive. Also tried 300 GB IDE (still have IDE) of which I now have Debian Lenny installed. I have a PCI/IDE  controller card to my hard drive rather than using the IDE controller directly from the motherboard. I use that for my DVD/ROM.  PCI controller cards were a problem in the past for many *nix OSes but should not be now.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------
I will be glad to get back to Ubuntu so I can stop using the chown command, and even that does not work all the time. It's like Debian is really that locked down.
I like to plug in a removable drive and see it right on my desktop both in read-write format

---

### Post by linux18 on 2010-08-10
> **from_beyond said:**
> I tried a 750 GB IDE drive. Also tried 300 GB IDE (still have IDE) of which I now have Debian Lenny installed. I have a PCI/IDE  controller card to my hard drive rather than using the IDE controller directly from the motherboard. I use that for my DVD/ROM.  PCI controller cards were a problem in the past for many *nix OSes but should not be now.
try my remixed ubuntu distro if your connected via ethernet cable

---

### Post by oleink on 2010-08-11
> **from_beyond said:**
> I tried a 750 GB IDE drive. Also tried 300 GB IDE (still have IDE) of which I now have Debian Lenny installed. I have a PCI/IDE  controller card to my hard drive rather than using the IDE controller directly from the motherboard. I use that for my DVD/ROM.  PCI controller cards were a problem in the past for many *nix OSes but should not be now.

Alright well maybe you had a faulty download not a faulty drive (either of your drives.)  Try making a fresh cd from either the Ubuntu website source or a different source than you originally tried.  I got a faulty disc before and went to the same download page and redid it and it worked afterword.  If the iso you downloaded is faulty and you tried more than one cd you will still have the errors because the iso is the problem

---

### Post by from_beyond on 2010-08-11
No my disks are not faulty tried too many of them. It must be a hardware related issue.

Ubuntu is the only *nix that got me off windows.

---

### Post by oleink on 2010-08-12
> **from_beyond said:**
> No my disks are not faulty tried too many of them. It must be a hardware related issue.

Ubuntu is the only *nix that got me off windows.

but did you try different disks with different iso

---

### Post by from_beyond on 2010-08-13
I bought a Ubuntu 10.04 disk today and gave it the smoke test. The following message:
"This CPU...has NX capabilities but is unable to use these protective features because the BIOS is configured to disable the capabilities.
Please enable this in your BIOS".
OK- I explored my BIOS Security settings and this feature is disabled under the Chassis Intrusion option and I don't have the option to enable it. My BIOS is about 4-5 years old. Therefore I discovered yet another reason why Ubuntu will not install.
Another problem is even though I ran memtest 86 , I did not run it for 48 hours which can give a better indication if my memory is problematic in installing the latest Ubuntu. Memtest is not always accurate--  not a opinion.
So I have two issues here to further investigate a  complicated OS install. It is not that Ubuntu is hard to install, it's just that the hardware requirements have gotten stiffer. I can find no other reason.

---

### Post by from_beyond on 2010-08-13
I tried a text based installation of Alternative Ubuntu 10.04. It installed flawlessly so now I am pretty sure the problem all along was bad memory which needs to be replaced. Thanks to the individual that suggested it to me!

---

### Post by oleink on 2010-08-15
> **from_beyond said:**
> I tried a text based installation of Alternative Ubuntu 10.04. It installed flawlessly so now I am pretty sure the problem all along was bad memory which needs to be replaced. Thanks to the individual that suggested it to me!

Awesome.  Good luck

---

