---
title: "Ubuntu 10.04 LTS hangs and crashes unexpectedly."
date: 2010-05-10
forum: General Help
---

### Post by doomguard88 on 2010-05-10
Well hello everyone.

I recently did a clean install of lucid lynx amd64 on my desktop computer.

After a some days of usage i started experiencing crashes or hangs.

Twice my computer crashed and rebooted immediately after.

3-4 times my computer hanged as in while listening to an on-line radio station music began to loop and the computer  become completely unresponsive.

The Apps i was running at that time i think were firefox vlc jdownloader ...

My question is: In the event that this isn't a hardware problem since windoz are fine, is there some logs i can post/look at or same other app that can help me resolve this??

Thank you for your help.

---

### Post by Legwan on 2010-05-10
That same problem for me.
I found that it usually involves "voice app" + wireless internet (watching youtube or speaking via skype) otherwise everything is fine.
If it matter I have 64bit version, my hardware is Compal FL90, internet via WPA2.
That problem had not happened with previous ubuntu, so I guess it might be connected with HAL removal
If You submitted a bug please give a link - I'll join.

---

### Post by ibrahim.k on 2010-05-10
I am having the same issues .. did it happen when installing google chrome ?
thats how i got this issues

---

### Post by Legwan on 2010-05-10
No, but it [chrome] was working - in fact it is on almost all the time.

---

### Post by Razzie on 2010-05-10
Same problem here, hangs randomly. 

It seemed to go away for a day when i set the fsck check to every time the system boots. but the system still hangs at random intervals.

Every (generic) kernel has the same problem, read a tip in another thread to install the rt kernel so trying that tonight.

Lucid lynx 
Acer aspire one A150

---

### Post by Razzie on 2010-05-11
Installed the RT Kernel, Booting seems to be a bit slower, kernel is also alot older but a havent experienced hangs anymore.

How to install a RT Kernel:
Open synaptics search for Linux rt.
Somewhere in the list you will find 
linux-headers-rt
linux-rt
linux-kernel-rt ( or something, not at home at the moment )

Install those and reboot, in the grub menu will be a new option indicating it is an RT kernel.
Start that and problems seem to be gone

---

### Post by kokonobs on 2010-05-11
I have the same problem. I'm running the 64bit version on a dell inspiron 1564 i3 core processor.

First time it i was streaming tvcatchup using xbmc and there was another stream in firefox. Everything hangs but the stream continues. Second time it was just the stream in xbmc. Just about an hr ago it was an online radio stream on firefox. (I may be wrong but in all cases i was also running on battery power)

---

### Post by Legwan on 2010-05-16
After last upgrades problem didn't happen any more ... hopefully it was solved.

---

### Post by DeMus on 2010-05-16
Stupid question: what is a RT kernel and how does it differ from the normal kernels supplied with Lucid?

---

### Post by pradeepthundiyil on 2010-05-16
Hi,

Its working perfect.. My issue was with my hard disk..

---

### Post by Roersma on 2010-06-14
Hi Razzie, I had the same problems and also installed de RT kernel. At first i thought it worked but after 2 days the same problems continued. What´s the kernel you are using now?

---

