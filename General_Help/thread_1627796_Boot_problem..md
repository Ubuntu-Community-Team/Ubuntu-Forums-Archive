---
title: "Boot problem."
date: 2010-11-21
forum: General Help
---

### Post by nu2this2 on 2010-11-21
Have a dual boot system, WinXp Home edition and Ubuntu Hardy Heron. Was recently on the internet using  windows when suddenly the computer shut down. Upon trying to restart, the screen was completely black with only a white cursor blinking in the upper left corner of the screen. I could not use the mouse at all and had to shut down with the power switch.

Usually when starting the computer, the screen displays "starting grump" or something to that effect then I can choose which O.S. I wish to use. That messege no longer appears, so now, not only can I not go into Windows I cannot boot Ubuntu. I tried to use my recovery disc for windows but the computer would not launch the cd. It would launch Ubuntu live cd however.

My question is, is there a way that I can use the live ubuntu cd to repair my grub launcher. My thinking is the grub enabled me to make the choice of which OS to use. If I can get back that capability, might I have my boot problem solved?

---

### Post by MisterGaribaldi on 2010-11-21
You should be able to boot from the Ubuntu CD by ensuring it is in the drive prior to your computer starting up. You may possibly need to verify your BIOS is set to a boot order with the DVD/CD drive first and your hard disk second. Most systems use F2 or DEL on boot to enter the BIOS. Where the setting will be varies widely, but usually looking around in the BIOS will eventually lead to the correct spot.

Also, you may want, depending on what your BIOS is configured to display, to take a look at the status page which shows attached hard drives and see if it is still seeing your HDD. If, for instance, the area showing your primary (and potentially a secondary) hard drive is blank, you could have a failed HDD.

---

### Post by nu2this2 on 2010-11-22
Yes the Live CD boots up. The installed version does not however.

Could there be something wrong in the grub boot launcher, or could I have a bad HDD?

---

### Post by nu2this2 on 2010-11-24
Anyone?

---

### Post by wilee-nilee on 2010-11-24
> **nu2this2 said:**
> Anyone?

Run the bootscript in my signature. Paste all the text from the generated file in code tags. Make code tags by opening the reply click on the # and paste the text in between.

Hard to say whether its the HD how old is it?

---

### Post by nu2this2 on 2010-11-24
Thanks I'll have to wade through this stuff. Not really to computer leterate.

I think the HDD is about 9 years old.

---

### Post by wilee-nilee on 2010-11-24
> **nu2this2 said:**
> Thanks I'll have to wade through this stuff. Not really to computer leterate.

I think the HDD is about 9 years old.

Just feel free to ask any questions. 9 years old is rather old but that doesn't necessarily mean it failed.

Were you running windows in a admin account? I wonder if you just didn't pick up some malware. A admin account is a rather exposed environment for any user especially a MS setup.

What was your AV protection? 

And did you have good passwords as well?

---

### Post by nu2this2 on 2010-12-01
Sorry for such a long time getting back, this is what I did.

Downloaded Ubuntu 10.0 and installed it. I couldn't believe it worked. Windows however will not load or boot up. I can't figure this out. Why windows won't load?

---

### Post by wilee-nilee on 2010-12-01
> **nu2this2 said:**
> Sorry for such a long time getting back, this is what I did.

Downloaded Ubuntu 10.0 and installed it. I couldn't believe it worked. Windows however will not load or boot up. I can't figure this out. Why windows won't load?

So from a booted live Ubuntu cd or thumbdrive lets see the **bootscript** read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

If you really want any help you will need to post this script.

The only other suggestion is in the Ubuntu installed terminal run.
```
sudo update-grub
```

---

