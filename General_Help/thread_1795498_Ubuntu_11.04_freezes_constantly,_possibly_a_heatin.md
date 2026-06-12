---
title: "Ubuntu 11.04 freezes constantly, possibly a heating issue?"
date: 2011-07-02
forum: General Help
---

### Post by Comokanu on 2011-07-02
I have an Acer Travelmate 630(14.1" model) running Ubuntu 11.04 and I have experienced a frequent amount of freezing. Usually when I log in, the login sound effect doesn't play, the cursor turns into a wheel which changes back to the normal cursor, then changes into the wheel, but frozen. At this point the computer has completely frozen, nothing moving, no input of any kind responisive, and I have to hard reboot. Several times after that the problem goes away and I am able to log in and use it normally.

I also experienced freezing when loading up Ubuntu Software Centre and using Firefox.

Sometimes after leaving it for a while, the problem is gone, but after an hour or two completely freezes again.

Everything on the machine is stock, apart from upgraded 1GB RAM and 60GB HDD. And I use an external monitor because the internal one has a damaged cable(replacement coming soon).

Are there anyways I can track down the problem? I have already uninstalled compiz and am running Ubuntu Classic mode.

I am happy to downgrade to 9.04 as that is compatible with my USB WiFi adaptor without doing complex stuff, but would like to solve the problem on 11.04.

Thank you in advance and I will provide further information when required.

---

### Post by Comokanu on 2011-07-02
Strange thing is, after cool down it loads fine and works for 20 minutes then locks up. I boot it up again straight after hard reboot, locks up at login, tried again immediately and logs in fine then works for another 20 minutes then locks up. 

I thought it was cooling because it always logs in fine after a good cool down but then why would I be able to log in successfully after a few tries?

Please help me.

---

### Post by wildmanne39 on 2011-07-03
> **Comokanu said:**
> Strange thing is, after cool down it loads fine and works for 20 minutes then locks up. I boot it up again straight after hard reboot, locks up at login, tried again immediately and logs in fine then works for another 20 minutes then locks up. 

I thought it was cooling because it always logs in fine after a good cool down but then why would I be able to log in successfully after a few tries?

Please help me.
Hi, it sure will not hurt to clean your system out good, I do mine every three months. Here is a link on freezing.
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

---

### Post by Comokanu on 2011-07-03
Well I've only installed it yesterday, but I'll look into the site and find the problem or at least make it better to use.

Thank you.

---

### Post by wildmanne39 on 2011-07-03
> **Comokanu said:**
> Well I've only installed it yesterday, but I'll look into the site and find the problem or at least make it better to use.

Thank you.Hi, your welcome, please let us know if the guide helps.

---

### Post by bouherve on 2011-07-12
I have the same Acer Travelmate 630 laptop.
I have experienced that freezing for a long time what ALL UBUNTU DERIVATIVES on kernel 2.6.32 (as far as I remember) and above. I tried Peppermint, Mint with the same problem.
This won't happen with OpenSuse, Mandriva (but they are heavy for this type of hardware), nor with Puppy, nor with PCLinuxOS.
Booting with noacpi, or acpi=ht, or nohz=off didn't help.

---

### Post by Spyderkid on 2011-07-12
basically if its heating up it would auto-shutdown not freeze

so maybe you've got a corrupt filesystem part? try noting what your doing when it freezes, that would help us solve the problem

---

### Post by Comokanu on 2011-07-19
I am sorry for leaving this thread for a week! Thank you all for the help. When the system freezes I have to hard reset.

It sometimes happens when loading Ubuntu Software Centre, FireFox and generally opening anything that will involve using a lot of processing(often freezes when multitasking). With all Ubuntu distro installers for 11.04, it always freezes similarly before completion. I therefore have to start from 10.11 and update to 11.04 from there. 11.04 is the only one that sometimes freezes upon login. 9.04 and 10.04 doesn't have this login problem but freezes when using it.

So it might be a kernel problem?

I'm currently having to run XP and run DSLinux as a virtual machine inside. It's working fine at the moment, would want to run it natively too, maybe as a multi boot.

Again, thank you for the help.

---

### Post by Comokanu on 2011-07-19
> **bouherve said:**
> I have the same Acer Travelmate 630 laptop.
I have experienced that freezing for a long time what ALL UBUNTU DERIVATIVES on kernel 2.6.32 (as far as I remember) and above. I tried Peppermint, Mint with the same problem.
This won't happen with OpenSuse, Mandriva (but they are heavy for this type of hardware), nor with Puppy, nor with PCLinuxOS.
Booting with noacpi, or acpi=ht, or nohz=off didn't help.
Really? I must try Puppy Linux then. Do you think it is possible for it to install alongside Windows XP through partitioning and GRUB? Does the installer handle that?

The reason I chose Linux is because most of them have the perfect compromise of functionality and speed. Even DSL can be expandable to suit modern uses since it's pretty much Debian.

And thank you for the information!

---

