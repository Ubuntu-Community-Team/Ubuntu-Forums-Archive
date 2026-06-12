---
title: "Whats' the fastest version of Edubuntu?"
date: 2009-09-27
forum: General Help
---

### Post by NinjaNumberNine on 2009-09-27
Hey, I want to set up an old computer for my little sisters to learn how to type and learn math. The computer I have in mind is an ancient Compaq that just allows 256 MB of RAM and has a 10GB HDD.What is the most practical edubuntu version for that hardware? The packaging is really deceptive. They say quite confidentally that even Kubuntu will run on 64MB, but 256 is recommended.. What a joke.


BTW I am downloading Edubuntu Dapper Drake (6.01) right now. :)


Thanks!


NinjaNumberNine

---

### Post by gali98 on 2009-09-27
What you might considering doing is installing xubuntu. This should be much faster than gnome (which in my experience is faster than KDE.)
Then you could install the edubuntu packages over that.
See here:
[http://edubuntu.org/Download](http://edubuntu.org/Download)
Under the heading "Educational Application Bundles" for the right packages.

As for the version (as in 9.04, 8.10 and so on)
I would definately go with the latest version, Juanty (9.04.)
There were significant improvements to boot time. 
Karmic, which comes out October 31, should be even faster.
Kory

---

### Post by akakingess on 2009-09-27
+1 , I had  quite a bit of luck with xubuntu running on an old machine with just 192 Mb of RAM, so I would think it should work well on yours.

---

### Post by NinjaNumberNine on 2009-09-27
Unfortunately, I can't very easily move the computer so I can't get it online...

---

### Post by NinjaNumberNine on 2009-09-27
> **gali98 said:**
> What you might considering doing is installing xubuntu. This should be much faster than gnome (which in my experience is faster than KDE.)
Then you could install the edubuntu packages over that.
See here:
[http://edubuntu.org/Download](http://edubuntu.org/Download)
Under the heading "Educational Application Bundles" for the right packages.

As for the version (as in 9.04, 8.10 and so on)
I would definately go with the latest version, Juanty (9.04.)
There were significant improvements to boot time. 
Karmic, which comes out October 31, should be even faster.
Kory

I thought the older the version the more it would have been made for older hardware...:lolflag:

---

### Post by gali98 on 2009-09-28
> **NinjaNumberNine said:**
> Unfortunately, I can't very easily move the computer so I can't get it online...
Oog. I know how that can be... But I still suggest installing Xubuntu... then transferring the debs for edubuntu stuff.

As for the older version... maybe... but with kernel enhancements, probably not. And really for older hardware you would need to go to the 2.4 kernel for any speedups (if any.)
DSL is based off the 2.4 kernel.
Kory

---

### Post by NinjaNumberNine on 2009-09-28
Thanks. Any suggestions for "what next" when I try to install Xubuntu 9.04 (to add the educational packages to) and it shows the Xubuntu loading logo for a few seconds, then says something about an APIC error and then drops to BusyBox? (I hate BusyBox, don't know how to work it :) )

---

### Post by gali98 on 2009-09-29
try booting it with the option "noacpi"
Check here for more details:
[https://help.ubuntu.com/community/BootOptions#Kernel%20Options](https://help.ubuntu.com/community/BootOptions#Kernel%20Options)
Kory

---

### Post by NinjaNumberNine on 2009-09-30
Done that, no change... :(
-That is, assuming you mean press f6 on boot and select "noacpi"
Otherwise, where do you type "acpi=force?"

---

### Post by earthpigg on 2009-09-30
hi,

perhaps you should consider combining apt-on-cd with a lightweight ubuntu derivative? (xubuntu really is not lightweight.)

use apt-on-cd on a computer with internet access to get all the educational software and whatnot that you want:

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

pick a distro listed [here]("http://wiki.lxde.org/en/Ubuntu#Ubuntu_variants_with_LXDE_pre-installed") or [here]("http://lightlinux.blogspot.com/2009/02/lightweight-ubuntu-derivatives-for-old.html") that looks good to you.

Spri is a maintained by a member of our forum community, Masonux is maintained by me, but Crunchbang is by far the most well known of those mentioned.



Another way you could do it, if you don't want to use apt-on-cd is to install all the software you want on a computer that ***does*** have internet access.... and then use remastersys to generate an .iso file and turn that system into an installable cd/dvd.

[http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)

---

### Post by gali98 on 2009-10-12
> **NinjaNumberNine said:**
> Done that, no change... :(
-That is, assuming you mean press f6 on boot and select "noacpi"
Otherwise, where do you type "acpi=force?"
Use that link I gave you. It explains everything.
Kory

---

### Post by NinjaNumberNine on 2009-10-12
> **earthpigg said:**
> hi,

perhaps you should consider combining apt-on-cd with a lightweight ubuntu derivative? (xubuntu really is not lightweight.)

use apt-on-cd on a computer with internet access to get all the educational software and whatnot that you want:

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

pick a distro listed [here]("http://wiki.lxde.org/en/Ubuntu#Ubuntu_variants_with_LXDE_pre-installed") or [here]("http://lightlinux.blogspot.com/2009/02/lightweight-ubuntu-derivatives-for-old.html") that looks good to you.

Spri is a maintained by a member of our forum community, Masonux is maintained by me, but Crunchbang is by far the most well known of those mentioned.



Another way you could do it, if you don't want to use apt-on-cd is to install all the software you want on a computer that ***does*** have internet access.... and then use remastersys to generate an .iso file and turn that system into an installable cd/dvd.

[http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)
Thanks, Earth Pig. That's a very informative post. I downloaded CrunchBang. (I looked at Masonux and Spri, but since I don't know how to make bricks and I'm not very spry, I jumped on the Crunchin Bangin bandwagon lol )  Anyway I got CrunchBang and installed it on the PC and then installed the edubuntu packages from the CD. Thanks, everyone! (You too Kory :))

---

