---
title: "Windows reinstall has me guessing"
date: 2010-06-26
forum: General Help
---

### Post by fooneyguy on 2010-06-26
I'm something of a linux newbie here so please forgive me. I first downloaded and installed ubuntu through wubi a couple of weeks ago. So I was happily tripple booting vista, xp and ubuntu. After a power outage I began having serious issues in vista. At first I believed it was a hardware problem but soon discovered that ubuntu was running fine. Well I formatted my vista and xp partitions, combined them into on partition and only reinstalled vista. I'm happy to report that vista runs great (well for windows anyway) but now it won't boot ubuntu much to my dismay. I've looked around but I haven't found a solution to my particular problem and I don't know enough about the command line to just start poking around without fouling things up. Is there a way to get ubuntu booting again without a complete reinstall? Thanks for any help.

I should add that I installed ubuntu onto a separate partition which I left alone when I reinstalled vista. I'm looking for a solution to bet back into ubuntu.

---

### Post by Pollox on 2010-06-26
It sounds like you just need to reinstall grub so all your operating systems appear on it?  Check out these links:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by thefallofroy on 2010-06-26
I could be wrong, but I think that when you formatted your partitions, it completely wiped wubi and ubuntu. If that's the case then the only thing you can do is re-install unfortunately.

---

### Post by wilee-nilee on 2010-06-26
Post the bootscript in my signature so we can see your setup use the code tags as described.

---

### Post by slooksterpsv on 2010-06-26
Reinstall unless you installed Wubi on a separate partition thats still there, which I'm not sure how to fix that.

Wubi creates files for the OS and know how to load it, kind of like how VirtualBox creates a Virtual Hard Drive (VHD).

I'd reinstall Wubi, won't hurt.

---

### Post by cbilljones on 2010-06-26
Boot a live cd, see if your ubuntu is still there. If so, go ahead and reinstall grub; links are provided by above poster:



[https://help.ubuntu.com/community/Gr...0from%20LiveCD](https://help.ubuntu.com/community/Gr...0from%20LiveCD)
[https://help.ubuntu.com/community/Re...tallingWindows](https://help.ubuntu.com/community/Re...tallingWindows)

---

### Post by fooneyguy on 2010-06-26
So I've figured it out. When I reinstalled vista I did leave the partition with ubuntu alone so all the data was still there. 

So I backed up my f.disk and reinstalled wubi then swapped the new f.disk with the one I had backed up. And Bam!!! I'm up and running again. Linux is awesome :)

---

### Post by slooksterpsv on 2010-06-27
> **fooneyguy said:**
> So I've figured it out. When I reinstalled vista I did leave the partition with ubuntu alone so all the data was still there. 

So I backed up my f.disk and reinstalled wubi then swapped the new f.disk with the one I had backed up. And Bam!!! I'm up and running again. Linux is awesome :)

Congrats. Linux is amazing and the best OS I've used.

[Solved]

---

### Post by ronnielsen1 on 2010-06-27
> congrats. Linux is amazing and the best os i've used.
+1

---

