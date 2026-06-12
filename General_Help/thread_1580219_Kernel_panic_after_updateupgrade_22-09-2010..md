---
title: "Kernel panic after update/upgrade 22-09-2010."
date: 2010-09-23
forum: General Help
---

### Post by CromagDK on 2010-09-23
Yesterday i was prompted by my update manager to update some packages.
I really don't remember which but i updated.

After reboot the box now kernel panics.
I don't believe i get a ubuntu splash screen, and at this point i can't figure out how to get to my grub, in case a kernel was upgraded and it's possible to boot to different kernel.

i noticed some words like 'mantis', 'oops' and 'dvb_core' was a part of the text i get on the screen.

Can this be because of a dvb* upgrade that breaks something important ?

If needed, i should be able to boot via liveCD, or i could take a picture of the errors.

i could use some hints here i must say.

---

### Post by sikander3786 on 2010-09-23
Press and hold down the Shift key as soon as the computer gets past the Bios screen. It will pop up the Grub menu. Select some other kernel I think at no. 3 at see if it still panics.

---

### Post by CromagDK on 2010-09-23
I have tried pressing shift quite many times from boot, but i still get the kernel panic.
/Cromag

---

### Post by sikander3786 on 2010-09-23
Does the Grub menu show up? Are you able to select an older kernel?

---

### Post by CromagDK on 2010-09-23
Sorry, i forgot to write that.
No i don't get a grub menu.

Nothing happens other than bios splash, black screen, and then kernel panic.

/cromag

---

### Post by sikander3786 on 2010-09-23
> I have tried pressing shift quite many times

You need to press and hold it down not press it frequently. Hold it as soon as you see your Bios screen until you see the Grub menu.

---

### Post by CromagDK on 2010-09-23
> **sikander3786 said:**
> You need to press and hold it down not press it frequently. Hold it as soon as you see your Bios screen until you see the Grub menu.

Ok, i'll give it a go.
/cromag

---

### Post by CromagDK on 2010-09-23
> **CromagDK said:**
> Ok, i'll give it a go.
/cromag

That does not give me a grub menu.
It's just noisy via the speaker, and throws kernel panic.

/Cromag

---

### Post by CromagDK on 2010-09-23
Shift is the button to hold and then grub menu will load.
I did that and found the kernel, and it does not seem to be updated as only one kernel 2.6.32.24 and the recovery was visible.
I tried the recovery, but i get kernel panic once again.

/Cromag

---

### Post by undecim on 2010-09-23
I always have to use the right shift to get to the grub menu. Left shift never works.

---

### Post by CromagDK on 2010-09-23
> **undecim said:**
> I always have to use the right shift to get to the grub menu. Left shift never works.

My left shift worked fine.
Did you read my last message ? :)

---

### Post by CromagDK on 2010-09-23
i've mounted my disc on a live system and get the following on my /var/log/apt/history.log

Start-Date: 2010-09-20  19:53:56
Upgrade: linux-image-2.6.32-24-generic (2.6.32-24.42, 2.6.32-24.43), nvidia-current (260.19.04-0yavdr0, 260.19.06-0yavdr0), l
inux-headers-2.6.32-24 (2.6.32-24.42, 2.6.32-24.43), linux-headers-2.6.32-24-generic (2.6.32-24.42, 2.6.32-24.43), nvidia-cur
rent-modaliases (260.19.04-0yavdr0, 260.19.06-0yavdr0)
End-Date: 2010-09-20  19:56:29

Start-Date: 2010-09-21  20:10:46
Upgrade: bzip2 (1.0.5-4, 1.0.5-4ubuntu0.1), libbz2-1.0 (1.0.5-4, 1.0.5-4ubuntu0.1), php5 (5.3.2-1ubuntu4.2, 5.3.2-1ubuntu4.5)
, s2-liplianin-dkms (0~20100603.14629, 0~20100920.15345), dpkg (1.15.5.6ubuntu4.1, 1.15.5.6ubuntu4.3), flashplugin-installer
(10.1.82.76ubuntu0.10.04.2, 10.1.85.3ubuntu0.10.04.1), dpkg-dev (1.15.5.6ubuntu4.1, 1.15.5.6ubuntu4.3), php5-mysql (5.3.2-1ub
untu4.2, 5.3.2-1ubuntu4.5), libapache2-mod-php5 (5.3.2-1ubuntu4.2, 5.3.2-1ubuntu4.5), php5-common (5.3.2-1ubuntu4.2, 5.3.2-1u
buntu4.5)
End-Date: 2010-09-21  20:13:18

Start-Date: 2010-09-22  13:46:04
Upgrade: apache2-utils (2.2.14-5ubuntu8, 2.2.14-5ubuntu8.2), apache2.2-bin (2.2.14-5ubuntu8, 2.2.14-5ubuntu8.2), apache2-mpm-
prefork (2.2.14-5ubuntu8, 2.2.14-5ubuntu8.2), apache2.2-common (2.2.14-5ubuntu8, 2.2.14-5ubuntu8.2), s2-liplianin-dkms (0~201
00920.15345, 0~20100921.15345), libssl-dev (0.9.8k-7ubuntu8, 0.9.8k-7ubuntu8.1), libssl0.9.8 (0.9.8k-7ubuntu8, 0.9.8k-7ubuntu
8.1), openssl (0.9.8k-7ubuntu8, 0.9.8k-7ubuntu8.1)
End-Date: 2010-09-22  13:48:19


i'm pretty sure i rebooted before the update from the 21st, but im not sure. So so all of the above actually could be the problem. How do i determine where my problem is ?

Thanks :)

/Cromag

---

### Post by CromagDK on 2010-09-23
Bump.

---

### Post by sikander3786 on 2010-09-23
> 
'mantis', 'oops' and 'dvb_core'

From that statement, I just can guess that you've a tv tuner card and the error is referring to it. If you've got one, try to remove it and reboot because faulty hardware might be a cause for kernel panic. Also try to  run memtest from the Grub menu and see if any RAM module has run faulty in the recent days.

---

### Post by CromagDK on 2010-09-23
> **sikander3786 said:**
> From that statement, I just can guess that you've a tv tuner card and the error is referring to it. If you've got one, try to remove it and reboot because faulty hardware might be a cause for kernel panic. Also try to  run memtest from the Grub menu and see if any RAM module has run faulty in the recent days.

I'll give it try. Thanks :)
/Cromag

---

### Post by CromagDK on 2010-09-23
that did the trick.
Now i need to "roll back" i guess somehow, as the card worked before the upgrades :)

Thanks :)

/Cromag

---

### Post by sikander3786 on 2010-09-23
> **CromagDK said:**
> that did the trick.
Now i need to "roll back" i guess somehow, as the card worked before the upgrades :)

Thanks :)

/Cromag
Glad to hear that. Check that card on some other PC/OS and see if it works there. If so try to plug it in Ubuntu in a different PCI slot. If it doesn't take it to a hardware professional. Sounds more like a hardware problem to me than the updates.

Regards.

---

### Post by CromagDK on 2010-09-23
> **sikander3786 said:**
> Glad to hear that. Check that card on some other PC/OS and see if it works there. If so try to plug it in Ubuntu in a different PCI slot. If it doesn't take it to a hardware professional. Sounds more like a hardware problem to me than the updates.

Regards.

The card worked fine prior to the updates i must say.
/Cromag

---

### Post by sikander3786 on 2010-09-23
Might be a coincidence. Some chip on the card burnt itself exactly during the update process. May be, it was bored by the updates already and waiting for revenge LOL. :-)

Not sure though. Just check it and we'll have the answer then.

---

### Post by Drikus on 2010-09-26
Found this on google, while having oopse of simular sort. Pinned it down to s2-liplianin-20100921.15345, not sure where you did get it but something is seriously broken in that package.

---

### Post by sikander3786 on 2010-09-26
Try downgrading s2-liplianin from Synaptic. Search for s2-liplianin, select it and from the Package menu, click Force Version and select the one that was being used previously.

Lets hope it fixes your card.

---

### Post by CromagDK on 2010-09-26
I'm "sorry" to say, that i went reinstalling instead.
10.10 uses kernels which supports my card, not sure if it is called natively in this situation.

But i just need to modprobe mantis, and the card works, no panics no other problems.

/cromag

---

