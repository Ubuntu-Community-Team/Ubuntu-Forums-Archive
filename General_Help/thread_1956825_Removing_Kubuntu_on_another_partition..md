---
title: "Removing Kubuntu on another partition."
date: 2012-04-11
forum: General Help
---

### Post by Little Beast on 2012-04-11
Hi,

I used to have a dual boot system (Kubuntu + Windows) with 2 partitions on 1 hard drive.
I recently added a new (additional) SSD and installed a new, fresh Kubuntu on it which means I now have a triple boot system. Now I want to remove my 'old' Kubuntu, but I'm not sure how to do this. Is it just a matter of formatting that partition ?
And what about Grub ? Will it detect this and update its menu automatically ? If not, can you tell me how I have to modify my grub menu ?

Thanks in advance

---

### Post by PhantomTurtle on 2012-04-11
I think that depends on if you decided not to overwrite grub when you installed Kubuntu for a second time. If you did not make a /boot partition for Kubuntu the second time you installed and installed grub, then you should be fine with just deleting that partition. If something goes wrong however you can just recover grub using this tutorial: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"). I know it is for Ubuntu, but it will work with the Kubuntu Live CD as well, so don't worry.

---

### Post by Little Beast on 2012-04-12
OK, so I deleted this partition and rebooted my system. The Grub menu still showed 3 operating systems, but I could boot Kubuntu on my SSD. I restored Grub as you told me (I used the terminal way) and that did indeed the trick.

---

### Post by PhantomTurtle on 2012-04-12
> **Little Beast said:**
> OK, so I deleted this partition and rebooted my system. The Grub menu still showed 3 operating systems, but I could boot Kubuntu on my SSD. I restored Grub as you told me (I used the terminal way) and that did indeed the trick.

If the entry for the old install is still there, then just update grub(but it seems like you did). So it's all good now? If so mark the thread solved.

---

### Post by Little Beast on 2012-04-12
> **PhantomTurtle said:**
> If the entry for the old install is still there, then just update grub(but it seems like you did). So it's all good now?
Yes, thank you.
> **PhantomTurtle said:**
> If so mark the thread solved.
Done ;)

---

