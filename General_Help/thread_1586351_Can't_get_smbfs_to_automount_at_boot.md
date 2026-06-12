---
title: "Can't get smbfs to automount at boot"
date: 2010-10-01
forum: General Help
---

### Post by ar1stotle on 2010-10-01
Alright, I'm trying to get some of my NAS storage to mount on my xubuntu 10.04 box at boot time. I have it in fstab, and when I run 

$sudo mount -a

it mounts just fine. However, I have to run that manually, I can't get it to just mount at boot time. Here's the entry from my fstab:

//192.168.0.23/Seagate\040FreeAgent\040Pro/Program\040Files/StepMania/Songs /mnt/smsongs	smbfs	auto,rw,user	0	0

So like I said, manually running mount -a works fine, I just can't get it to do it automatically at boot time. I feel like the auto option should take care of that, and that's what I've read around here, but it's just not working. Any ideas? Would Xubuntu do anything slightly differently?

---

### Post by ar1stotle on 2010-10-02
I was just thinking, is it possible that it's running the mount before the network connections are set up?

---

### Post by ar1stotle on 2010-10-02
Well, the answer did end up being here, just had to look for the right thing. It does appear that trying to mount before the network is up was the problem, so for anyone else who runs into this thread, this post yielded the solution:

[if-up.d script]("http://ubuntuforums.org/showpost.php?p=9313917&postcount=29")

---

