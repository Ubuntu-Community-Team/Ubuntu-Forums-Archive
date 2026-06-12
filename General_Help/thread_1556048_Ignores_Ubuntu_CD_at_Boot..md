---
title: "Ignores Ubuntu CD at Boot."
date: 2010-08-18
forum: General Help
---

### Post by wizarddrummer on 2010-08-18
Hi,

Strange problem.

Old HP Compac 220 mt
1st, 2nd, 3rd Boot Device is CD. (figured I'd give it 3 tries to find it)
4th Boot Device is HD.

Start machine with Ubuntu CD (machines skip on to HD and loads XP - this CD works on another machine)
Start machine with Mint CD (machine skips on to HD and loads XP - this CD also works on another machine)
Start machine with XP CD I get press any key to boot from CD.

Anyone have any ideas?

Thanks...

---

### Post by plucky on 2010-08-19
> **wizarddrummer said:**
> Hi,

Strange problem.

Old HP Compac 220 mt
1st, 2nd, 3rd Boot Device is CD. (figured I'd give it 3 tries to find it)
4th Boot Device is HD.

Start machine with Ubuntu CD (machines skip on to HD and loads XP - this CD works on another machine)
Start machine with Mint CD (machine skips on to HD and loads XP - this CD also works on another machine)
Start machine with XP CD I get press any key to boot from CD.

Anyone have any ideas?

Thanks...


Sounds like broken CD drive.

---

### Post by anirudhtomer on 2010-08-19
I think there is a problem with the CD's boot sector.
If boot sector had been right & some other sector would have been bad then would have faced problem in the middle of the installation but since you are not even able to boot I think your boot sector is corrupted,

---

### Post by wizarddrummer on 2010-08-21
> **anirudhtomer said:**
> I think there is a problem with the CD's boot sector.
If boot sector had been right & some other sector would have been bad then would have faced problem in the middle of the installation but since you are not even able to boot I think your boot sector is corrupted,

Thank you very much for taking the time to respond. 

Even though I'm almost 60 and I have been speaking English for most of that time, I must not be able to communicate effectively. It is my fault that I did not make myself completely understood.

I would ask you to please read these sentences again... I tried to use brief descriptions my post. Here is the expanded version that leaves little to anyone's imagination.

[COLOR=Blue]**1)**[/COLOR] I put the **[COLOR=Red]UBUNTU [/COLOR]**CD into the CD-ROM Drive of this Old HP Compac 220 mt machine.
The BIOS (which has 4 Boot options) is configured to have the first 3 options to boot from the CD. I am giving the boot process 3 chances to try and find the CD to boot from.
When I turn the machine on or restart the machine, the boot process [COLOR=DarkGreen]**SKIPS **[/COLOR]over the CD. IT DOES NOT RECOGNIZE THAT THE CD IS IN THE DRIVE and it loads XP from the Hard Drive.  [COLOR=Red]******PLEASE NOTE ***** THE UBUNTU CD works on another machine that I have here in my house[/COLOR].

[COLOR=Blue]**2)**[/COLOR] I put the **[COLOR=Red]MINT [/COLOR]**CD into the CD-ROM Drive of this Old HP Compac 220 mt machine.
The BIOS (which has 4 Boot options) is configured to have the first 3 options to boot from the CD.  I am giving the boot process 3 chances to try and find the CD to boot from.
When I turn the machine on or restart the machine, the boot process [COLOR=DarkGreen]** SKIPS **[/COLOR]over the CD. IT DOES NOT RECOGNIZE THAT THE CD IS IN THE DRIVE and  it loads XP from the Hard Drive.  [COLOR=Red]******PLEASE NOTE ***** THE MINT CD works on another machine that I have here in my house[/COLOR].

[COLOR=Blue]**3)**[/COLOR] I put the [COLOR=Red]**XP **[/COLOR]CD into the CD-ROM Drive of this Old HP Compac 220 mt machine [COLOR=Purple]**[COLOR=Black]and the machine responds with[/COLOR]_[COLOR=Navy] [/COLOR][COLOR=Navy]press any key to boot from the CD.[/COLOR]_**[/COLOR]

[B]The CD drive works perfectly when I am using the machine when XP has loaded.
[/B]
As I stated, both CD's work in another machine. The likelihood that both the UBUNTU CD and the MINT CD that work in another machine would suddenly have a Boot sector problem at the same time is, in my guestimation, a very slim chance.

So my question remains, why is this happening?

At this point, the way things have been going for me I'm thinking Spirits or Witches.

---

### Post by varunendra on 2010-08-21
Maybe not convenient, but what I'd try first in this **special case** is to interchange the optical drives between the current computer & the one on which the Ubuntu CD worked, and retry to boot. Only then, based on the result, I may be able to **guess** the reason or make an assumption.

If you don't find it too inconvenient, please give it a try & post the results.


A couple of years ago I wrote a data DVD (1x or 2x was the writing speed) on an old samsung writer. Ever since then no other DVD writer but that old one detects it as written. Every other (any brand- including samsung itself!) writer would detect it as empty with 4.7GB available space, but any attempt to write on it would fail. Put it back into the same old writer and it would be read instantly & smoothly.

Although CDs use much simpler & almost identical techniques for writing, I guess something similar as above may be a reason for your problem.

---

