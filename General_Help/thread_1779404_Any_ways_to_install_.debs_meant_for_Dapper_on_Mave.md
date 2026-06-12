---
title: "Any ways to install .debs meant for Dapper on Maverick?"
date: 2011-06-10
forum: General Help
---

### Post by 3602 on 2011-06-10
In a desperate attempt to play Tomb Raider, I have now Open Raider, a very old and seemingly abandoned open-source project.
The .deb is only for i386, so:
```
sudo dpkg -i --force-architecture
```But I have dependency problems. It needs old packages such as *libopenal0* which cannot be found in apt, Synaptic or Aptitude.
Tried to install the corresponding Windows game in Wine but I get a black screen. Is it so hard for a Linux user to enjoy watching Lara jumping up and down?

Thank you very much!

---

### Post by Dave_L on 2011-06-10
Have you looked for the old packages at [http://packages.ubuntu.com/](http://packages.ubuntu.com/) ?

---

### Post by 3602 on 2011-06-10
> **Dave_L said:**
> Have you looked for the old packages at [http://packages.ubuntu.com/](http://packages.ubuntu.com/) ?
I am currently in the process of waiting God knows how much time to move and shrink my *sda1 *so maybe I can get XP installed and running *then finally, maybe,* I can enjoy Tomb Raider. If that doesn't work, well, I'll go check. Thank you.

---

### Post by hhh on 2011-06-10
@3602, be warned that it's recommended to install Windows first, run a thorough disc defrag, shrink Windows, let Windows reboot and run it's chkdsc, and then install Ubuntu so that Grub2 will handle bootloading. Windows will not automatically recognize your Ubuntu partition, so this page hopefully will help you recover Grub...
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by 3602 on 2011-06-10
Thank you. I already did that yesterday (or was it before yesterday? Hmm...) and know how to recover Grub(2). Thank you. Whole thing is that back then, Windows won't boot. Just won't. Says Windows has failed to start normally or somethin' along those lines. I figure that's because the NTFS slice is caked between my *sda1* and the Linux-extended. So I'm moving the entire *sda1* so the new NTFS slice can be at one end. Hmm cake. The cake is a lie, no? Well I ain't GLaDOS so how would I know that. Did you know that GLaDOS also gives BSoD's? I bet she doesn't need to play Tomb Raider...

---

### Post by 3602 on 2011-06-10
Alright. Windows is installed, is booting, and I just need to port the drivers over there, download DX and start gaming.
Marking solved because a "workaround" is used.

---

