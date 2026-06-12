---
title: "System unresponsive"
date: 2010-10-30
forum: General Help
---

### Post by zane73 on 2010-10-30
I'm very new to Linux.  I've tried it a few times in the past only to get frustrated and remove it.  I have installed 10.10 on an IBM T30 laptop and all was working very good, until I decided to install AVG antivirus.  Not sure if this is what messed things up though.

Anyway, the system boots fine and comes up to a 'Unlock Login Keyring' screen, but the hard drive starts grinding away and the system becomes unresponsive.  The cursor moves very slowly.  It is like the system has a task running in the background that is stuck in a loop.  I have left it for several hours only to come back and find it still beating the crap out of the hard drive.  I have to cut the power as I can't shut it down gracefully.

Any ideas on what I should try?  I'm thinking about reinstalling it, but would rather figure out what is wrong and fix it.  I need this to work as I need it for a college class I'm taking.

Any help will be greatly appreciated!

---

### Post by 73ckn797 on 2010-10-30
Have you removed AVG? There is Clam Anti-virus available in Synaptic Package Manager. Anti-virus is really not needed with Linux unless you have Windows in a dual boot or virtual box setup.

---

### Post by zane73 on 2010-10-31
> **73ckn797 said:**
> Have you removed AVG? There is Clam Anti-virus available in Synaptic Package Manager. Anti-virus is really not needed with Linux unless you have Windows in a dual boot or virtual box setup.

I'd love to try and remove it, but the system is unresponsive...  I can't do anything.  Is there a Safe Mode like in Windows that I can boot into?  And, if so, how do I remove it?  Remember, I'm very new to this, but need to learn as much as possible because of the Survey of Operating Systems college class I'm taking.

---

### Post by 73ckn797 on 2010-10-31
Are you able to see the grub boot menu? If your system starts and goes directly to Ubuntu, you can, while the boot process is going on, press any key and the boot menu should appear. From there select the recovery mode and use one of the options from there. I do not recall all of them so you will have to find the one that seems most applicable. Maybe someone else has that info immediately available.

---

### Post by zane73 on 2010-10-31
> **73ckn797 said:**
> Are you able to see the grub boot menu? If your system starts and goes directly to Ubuntu, you can, while the boot process is going on, press any key and the boot menu should appear. From there select the recovery mode and use one of the options from there. I do not recall all of them so you will have to find the one that seems most applicable. Maybe someone else has that info immediately available.

Not sure what I just did, but my 10.10 system appears to be fixed now.  I forced a shutdown by holding the power button and restarted it and just kept pressing random keys while it rebooted.  Logged in and started Synaptic Package Manager and removed AVG.  Rebooted again and all is well now!

I have no clue what AVG was doing, but it was seriously hammering away at my hard drive and had the system in such a screwed up state.  Lesson learned... no AVG Anti-Virus needed on Ubuntu 10.10!!!!

Thanks to all that replied!  I'm sure I'll have more questions as I delve into this more.

---

### Post by Omnomnom on 2010-10-31
According to [this,]("http://brainstorm.ubuntu.com/idea/14795/")
your gonna have to reinstall Ubuntu. You really don't need antivirus programs unless it's a shared computer and if you're smart about where you visit online you aren't really at risk.

---

### Post by Omnomnom on 2010-10-31
> **zane73 said:**
> Not sure what I just did, but my 10.10 system appears to be fixed now.  I forced a shutdown by holding the power button and restarted it and just kept pressing random keys while it rebooted.  Logged in and started Synaptic Package Manager and removed AVG.  Rebooted again and all is well now!

I have no clue what AVG was doing, but it was seriously hammering away at my hard drive and had the system in such a screwed up state.  Lesson learned... no AVG Anti-Virus needed on Ubuntu 10.10!!!!

Thanks to all that replied!  I'm sure I'll have more questions as I delve into this more.
Oh wow haha, glad that happened. No need to reinstall after all! :)

---

### Post by zane73 on 2010-10-31
> **Omnomnom said:**
> Oh wow haha, glad that happened. No need to reinstall after all! :)

Yeah, I'm very happy I didn't have to reinstall.  I was very close too, I had the install CD ready to go and everything.  

I just rebooted again and everything seems normal again.  It's such a relief to not have the hard drive spinning away like crazy!  It was driving me nuts hearing it!!

Again... Thanks to all!!

---

### Post by 73ckn797 on 2010-10-31
I have experienced many problems, usually self inflicted, and found that Ubuntu can fix itself in so many ways. The recovery mode accessible from the boot menu has kept me from several re-installations or purchasing new hard drives when things looked as if there was a hardware problem. Windows was not always so "pliable" in how it repaired problems.

Enjoy Ubuntu!!

---

