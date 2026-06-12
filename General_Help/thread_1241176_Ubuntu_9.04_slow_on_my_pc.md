---
title: "Ubuntu 9.04 slow on my pc"
date: 2009-08-15
forum: General Help
---

### Post by afroze9 on 2009-08-15
My problem:
I'm an ubuntu noob and dont know anything about it.
But i do know that its not supposed to run slow on my pc.
The problem is that right after installation of 9.04 it was kind of lagging, even the mouse cursor.
But that didnt happened when installed 8.10. (yes i tried to use it for 2 days)
My system:
Intel pentium 4 2.66 ghz
512 mb ram
120 gb hdd
Nvidia geforce 4 mx graphics card

But it runs fine on my laptop which is:
Intel Pentium 4 1.4 ghz
512 mb ram
40 gb hdd
Ati radeon 9600 graphics card

Any help would be really appreciated.

---

### Post by afroze9 on 2009-08-16
Come on now.
Please someone reply.

---

### Post by ashwinhgtx on 2009-08-16
Try turning off Desktop Effects. Right click on the desktop, select Change Desktop Background, go to the Visual Effects tab and then select None.
After this try installing the correct driver for your nvidia card.

---

### Post by afroze9 on 2009-08-18
Heres the thing:
I said it happened right after i installed it.
I even saw the desktop effects settings and they were off already.

About installing the driver:
I went to System>Administration>Hardware Drivers and installed the nvidia driver from there after my pc rebbots it gives an error that the driver cannot be loaded or something and now ive uninstalled the driver again.

---

### Post by bodyharvester on 2009-08-18
okay, this is probably not an option but did you re-install 9.04?

im sure in administration or preferences there is a "system testing" thing which tests your system and asks for feedback on what's happening, try that, if nothing else you'll be helping the developers

hope you get it sorted soon

- joe

---

### Post by afroze9 on 2009-08-19
I tried reinstalling but it didnt work and i get the same problem.
While using the system test utility i noticed that i dont hear sound from my speakers but from the internal beeping sound.

---

### Post by Cameron.Bingham on 2009-08-19
Looking at your computers specs you only have 512mb of RAM.
As Ubuntu gets better it's going to require more RAM just like anything else.

I'd recommend either downgrading or getting more RAM. :)

RAM is usually pretty cheap to buy.
Also one may run better because even though they have the same RAM one may have a better system.

So just try to upgrade your RAM if possible.

---

### Post by t0p on 2009-08-19
> **Cameron.Bingham said:**
> Looking at your computers specs you only have 512mb of RAM.
As Ubuntu gets better it's going to require more RAM just like anything else.

I'd recommend either downgrading or getting more RAM. :)

Pay no attention to this!   512MB is plenty!  I run Jaunty on a machine with 512MB and it's okay.  True, I do intend to add more - I fancy 2GB - but that isn't down to bad speed issues.  I'm just one of those "bigger is better" people.  But that doesn't mean bigger *is* better.  Plenty of chicks have told me that "size doesn't matter".

---

### Post by yeeeev on 2009-08-19
Can you try to run "top" from a terminal and post the output here?

---

### Post by NotJustANewbie on 2009-08-19
Download and run "powertop" as sudo.
It'll show you your top memory / power hogs.
Then run "ps -e" to find the ID of these processes and then "kill -9 XXXX" where XXXX is the ID of the memory hogging processes.  Just make sure you don't kill and necessary processes for Ubuntu to run ;)

---

### Post by afroze9 on 2009-08-19
Thanks for all the replies
I figured out the problem
I said that my cursor especially wasnt working right.
Turns out it was a problem with my mouse though it was running great in xp. I just had a thought and thought about changing the mouse. Now it runs fine. Though i still had problems with the graphic card. So i installed kubuntu in its place and all is fine.

Thanks again.

---

