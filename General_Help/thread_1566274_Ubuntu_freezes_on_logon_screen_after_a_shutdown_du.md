---
title: "Ubuntu freezes on logon screen after a shutdown during kernel update"
date: 2010-09-02
forum: General Help
---

### Post by progre55_icky on 2010-09-02
Hi guys,

A while ago, I was applying the new kernel updates (I guess 2.6.32-24, or the one after it.. well, the latest generic update) and accidentally powered off my laptop. And now it wont come up. It comes to the logon page, and neither the keyboard, nor the mouse work. Cant even switch to the TTYs. 
When I boot with the recovery mode, I just see a black screen (probably the TTYs dont work) but after "processing" some time, nothing happens. Not sure if the keyboard works, as I cannot turn on/off the capslock switch, but ctrl+alt+del works.

Tried booting with a live-cd and fsck'ing the drive, didnt help.

Any suggestions, please?

PS, some additional info that might help..
Sony Vaio nw series with ubuntu/kubuntu 10.04 on it.

Thanks in advance, truly appreciate!

---

### Post by dcstar on 2010-09-02
> **progre55_icky said:**
> Hi guys,

A while ago, I was applying the new kernel updates (I guess 2.6.32-24, or the one after it.. well, the latest generic update) and accidentally powered off my laptop. And now it wont come up. It comes to the logon page, and neither the keyboard, nor the mouse work. Cant even switch to the TTYs. 
When I boot with the recovery mode, I just see a black screen (probably the TTYs dont work) but after "processing" some time, nothing happens. .........!

Boot the previous kernel.

---

### Post by progre55_icky on 2010-09-02
> **dcstar said:**
> Boot the previous kernel.
Doesnt help, the same problem. I've got two kernels listed on grub (23 and 24), and two recovery modes for those. None work.
Probably the recovery mode brings up a TTY, but I just get a black screen, so my TTY seems to be broken..
Is there any way I can do anything using a live-cd? like, if I've got more than two kernels (havent deleted the old ones, so I guess I do) installed, then add them to the grub menu or smth? or how to load from another kernel?
Because I remember that on the previous kernel (**2.6.32-23**) the TTY was not working.. but on the one before, it was..

---

### Post by scotty boy on 2010-09-30
Fix described here: [http://ubuntuforums.org/showthread.php?p=9907252](http://ubuntuforums.org/showthread.php?p=9907252)

---

