---
title: "AMD Catalyst™ 12.6 Proprietary Linux x86 Display Driver"
date: 2012-06-28
forum: General Help
---

### Post by FishboyFive on 2012-06-28
AMD Catalyst™ 12.6 Proprietary Linux x86 Display Driver

Just Released No longer Beta 

Lets get this working so 99% of the world can install real drivers

---

### Post by QIII on 2012-06-28
Weren't the drivers before that real?

---

### Post by FishboyFive on 2012-06-29
no installing the drivers with jockey never work the updates driver 100% failed and has been broken the entire last two distros releases 


i wont even go there with you it makes me so angry Canonical does nothing to help with AMD drivers 

Linux is not windows 

AMD makes sure drivers work with windows because it owns 99% of the worlds desktop 

Linux can NOT be that picky it must make sure its OS works with the drivers AMD hands them . 

over time if they can show the world HEY we got good drivers / 3D support maybe they will get past that 1% desktop market and AMD will work more with linux 

its just the way it is

---

### Post by QIII on 2012-06-29
We've had this discussion before.  AMD is responsible for their drivers.  Canonical is under NO obligation to make the drivers work because they CANNOT change the proprietary driver.  The CANNOT make it work with Linux.  They CANNOT change it. They DO make Ubuntu work with the driver because they want Ubuntu to work with the hardware.   I'm not sure why this is so difficult to understand.  As I told you before, the driver in the repo IS THE AMD/ATI driver,  unadulterated and unmodified because Canonical CANNOT change it.  It is  closed source.  AMD is practically in bed with Canonical.  Every fourth and tenth month, Canonical gets the AMD/ATI driver BEFORE it is released for general consumption.

If you don't think the driver works on 12.04, come on over and look over my shoulder.    I will also show you that the driver does not yet work in 12.10 without  some fiddling.  It will by the time of release because by then all of  the necessary pieces will be in place -- because Canonical will make  sure they are.  The drivers have worked fine for a long time.  Installing from the repo via the command line does work.  Just because something does not work for YOU does not mean it doesn't work.  The Jockey installation SOMETIMES does not work for SOME users. The fglrx-updates package SOMETIMES does not work for SOME users.  For ME the driver works fine, but the Catalyst Control Center will not start.  That is ME.  That is not EVERYONE.

If you have a problem with this, become a MOTU (Master of the Universe) and ask to be responsible for the flgrx package to make sure it works properly.  [MOTUs]("https://wiki.ubuntu.com/MOTU/") are volunteers who ride herd over the Universe and Multiverse repositories. They are not Canonical employees; they are community members.  If something needs to be "fixed", offer to help "fix" it.

And read the ATI Driver Wiki in my signature.  If you read the wiki, you will see that I have even included a section on activating hardware acceleration, which many people mistakenly believe is not available with the Linux fglrx driver.

3D is even available for some AMD/ATI cards using the open source Radeon driver, which the Linux community DOES develop -- and AMD/ATI helps make that happen.  Also see that wiki link.

 You want to be helpful, I understand that.    I don't think you understand the issue and you simply need insight: you need to understand the  subject.

---

### Post by ka55o5 on 2012-06-29
> **FishboyFive said:**
> AMD makes sure drivers work with windows because it owns 99% of the worlds desktop
What do you mean, AMD or windows?.. With made-up numbers like that, it makes your thread/post look less credible. 

Anyway (on this ~1 year old, 2nd gen Sandy Bridge) I've got Nvidia GTS 450 (Palit) & with nvidia-settings, using the nvidia ppa x swat, for the first time (in history) I was able to switch over to *nix and have a working system - thanks to Ubuntu/Debian (12.04 Precise :))! [COLOR="Gray"]& TwinView![/COLOR]

> **QIII said:**
> [..] need to understand the subject.
I had found the explanation(s) to be a little vague. However it doesn't REALLY matter, because for example I am getting clipping, etc. -- (even) with Sync to VBlank, because of X limitations and because of many well-known reasons (& limitations); Only on one of the screens, because they are different: DVI & D-Sub of different size and different refresh rates.. 

One day this will be fixed, but we will need to develop / be using something other than X -- like everyone knows. Major things will have to evolve, ultimately for graphics to fully function in *nix. It's as simple as that, imo.

Hope I haven't bored you, too much, with this semi-useless post. =)

P.S.
Nvidia was/is on the up 'n up and I will never (need to) buy ATI again.

---

### Post by QIII on 2012-06-29
As a matter of objectivity, there roughly the same number of odd, unexplained behaviors with NVIDIA cards generating posts here as there are with ATI cards.

Both OEMs produce good hardware and both offer great Linux support.

But both also present problems for some users.

I'm happy NVIDIA cards work for you. That being the case, you should use NVIDIA cards.

---

