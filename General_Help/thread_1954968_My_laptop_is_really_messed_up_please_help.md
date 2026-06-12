---
title: "My laptop is really messed up please help"
date: 2012-04-09
forum: General Help
---

### Post by square519 on 2012-04-09
I am running ubuntu 11.10 on a toshiba satellite c55d-s5300 i have no windows partitions. my mouse and keyboard are unresponsive as soon as it boots up before you can interupt and go into bios. sometimes my wifi works but sometimes it doesnt. My computer freezes alot and everything just seems to not work correctly in some way including the graphics driver. what should i do from here

---

### Post by squenson on 2012-04-09
Has your laptop worked before you face your current issues?

If you don't have any data, I would suggest a complete re-install. You could also try to run Ubuntu from the CD, just to see if it works better. If not, my last idea is that you try another version of Ubuntu or Linux.

---

### Post by 2F4U on 2012-04-09
If your computer shows problems even before Ubuntu boots, I would suspect a hardware problem. Do you have the same problems if you connect external mouse and keyboard? If you can boot a liveCD I would first run memtest to verify that the RAM is ok.

---

### Post by QIII on 2012-04-09
A reinstall would be pointless, if it could be done at all, if the OP is experiencing hardware problems.

Even using the LiveCD would be impossible without input devices.  Furthermore, memtest can be run from the grub menu if the OP can get that far.

That said, memtest might be a good place to start.

Square519 -- what you can do for physical troubleshooting is limited with laptops.  You might be able to get access memory and reseat it and then run memtest.

However, I highly recommend that your first order of business be to back up all of your important data just in case your machine is about to bite the dust.  If you should have to get an RMA you won't want to send off data you won't get back.

If you can get the machine up long enough, get your important data to some external media before you have a disaster.

---

### Post by dylan07 on 2012-04-09
> **QIII said:**
> A reinstall would be pointless, if the OP is experiencing hardware problems.

True.

> **QIII said:**
>  Even using the LiveCD would be impossible without input devices. 
I would recomend trying to boot from live cd, this will check to see if it is a hardware issue. To check, simply boot the live CD, and if you can use your mouse, click "try ubuntu" and continue to test to see what works. I would highly recommend starting with this.

> **QIII said:**
> Furthermore, memtest can be run from the grub menu if  the OP can get  that far.
I suppose you can do that, but that is probably not the problem.

---

### Post by QIII on 2012-04-09
> **dylan07 said:**
> I suppose you can do that, but that is probably not the problem.

What it probably is or is not is speculative without either ruling out or confirming the possibility -- I'm sure you understand the nature of troubleshooting, right?

If the input devices are not working by the time the OS load process begins, it is not a problem with the OS.  The medium from which the OS loads, mechanical or optical, would not matter.

Hardware fault should always be eliminated when failures occur prior to OS load.

---

### Post by dylan07 on 2012-04-09
> **QIII said:**
> What it probably is or is not is speculative without either ruling out or confirming the possibility -- I'm sure you understand the nature of troubleshooting, right?

Yes, I do. A memtest would take awhile. And I figure, first step is find if it is hardware or software. I think first step is to attempt to boot into the LiveCD. If that fails, start diagnosing **hardware**. If it seems to work correctly, diagnose **software **issues.

---

### Post by QIII on 2012-04-09
> **dylan07 said:**
> Yes, I do. A memtest would take awhile. And I figure, first step is find if it is hardware or software. I think first step is to attempt to boot into the LiveCD. If that fails, start diagnosing **hardware**. If it seems to work correctly, diagnose **software **issues.

Again.  A fault is noted before OS load begins.

---

### Post by dylan07 on 2012-04-09
> **square519 said:**
>  my mouse and keyboard are unresponsive as soon as it boots up before you can interrupt and go into bios. Doesn't sound like a software problem. Nor a memory problem...
So, you are saying you can not even enter the BIOS, correct?

---

### Post by QIII on 2012-04-09
> **dylan07 said:**
> Nor a memory problem...

As you said, probably not.

---

### Post by dylan07 on 2012-04-09
Whoa! QIII ! I did not notice you are a "Kubuntu Development Release". I do apologize for not having faith in your troubleshooting!

---

