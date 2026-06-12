---
title: "Help! Error with File System."
date: 2010-01-29
forum: General Help
---

### Post by Ske7ch on 2010-01-29
Well, last night i was using Ubuntu just downloading music with Limewire and it was all working fine until I clicked on a a song to download and a message popped up saying something like "This computer doesnt have a file for Limewire downloads", im not exactly sure on how it said it but it had something to do with the File System. Since it was so late I just decided to leave it like that and deal with it in the morning.

I woke up and when I started Ubuntu and it says "File System not found", and something about pressing Control-D. Sorry for the lack of info I just dont remember exactly what it said, but like I mentioned above it has something to do with the File System that apparently isnt working.

I decided to re-install Ubuntu and it worked great, im using ubuntu right now but it doesnt have any of the setting and apps etc etc that I had on the other one. 

When I restart the computer and the dual-boot menu comes up it has 2 types of ubuntu, this one that works and the other one that everytime i click on it it keeps showing me the "File System not found".

Is there any way to fix my old version of Ubuntu 9.10?

And if I cant then how can I delete the damaged version of Ubuntu so it doesnt come up in the Dual-Boot screen? And I also have Windows 7 on it, how can I delete that one also? :lolflag:

Thanks!

---

### Post by Ske7ch on 2010-01-29
This is what it says:

On the Dual-boot screen theres the new Ubuntu I just installed that says:

Ubuntu Linux 2.6.31-17-generic
Ubuntu Linux 2.6.31-17-generic(recovery mode)

And the damaged one says:

Ubuntu Linux 2.6.31-17-generic(on/dev/sdas)
Ubuntu Linux 2.6.31-17-generic(recovery mode)(on/dev/sdas)

When I hit Enter on the damaged one a black screen appears showing me this message:

"Mount of File System failed.
A Maintenance shell will now be started.
Control-D will terminate this shell and retry
root@(my name here)-laptop~# (and here it gives me the option to type a command I guess)

---

### Post by Ske7ch on 2010-01-29
Well I did some more research and across the "fsck" command, so I ran that on the Terminal screen and fixed a couple of issues and now its working fine :cool:

But I still wish to delete the new Ubuntu I just installed and Windows 7. How can I do that?

Thanks!

---

### Post by audiomick on 2010-01-29
Here
[https://help.ubuntu.com/community/HowToRemoveWindows](https://help.ubuntu.com/community/HowToRemoveWindows)
**BUT**
the editing grub section applies to grub legacy. If your 9.10 was a fresh install, it will have Grub2
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Removing the superfluous Ubuntu is the same as removing the windows partition.

---

### Post by Ske7ch on 2010-01-29
Thanks!

---

