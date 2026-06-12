---
title: "Shared network folder contents not showing up over SSH"
date: 2011-06-20
forum: General Help
---

### Post by kamcknig on 2011-06-20
Hi all, I'm pretty new to Ubuntu and Linux in general.

I have a Windows maching with an attached NAS Drobo device. I have a linux maching running Ubuntu 11.04 and have edited the fstab file and been able to map the windows folders for the Drobo and they all mount up fine. On the Linux machine itself I can access these folders and run music/video files from them. But when I'm at another computer and SSH into my Ubunutu maching, I can see the mounted folders using the ls command but I can't see the contents of those folders. Anyone know why this might be happening?

Kyle

---

### Post by kamcknig on 2011-06-20
Ok, I've figured out a way to get it to work, but I don't know why it happens like this.

I know that when I am using the Ubunut machine itself, when it loads, I can log in, the mapped directories to the Drobo are shown in my /home dir where I put them. I can double-click them to go into them and the contents show up. 

I had rebooted the Ubuntu machine, then SSH'd in from another maching, and I can see the mapped drives, but can't see the contents. From the SSH'd machine I run mount -a, and then list the contents and it works.

So do the drives not get mounted at boot-up in the fstab file for some reason? Or is it just networked drives don't get mounted until specifically accessed from the GUI or forced to mount? How can I force it to completely mount at startup?

Kyle

---

### Post by Morbius1 on 2011-06-20
There is a bug which may or may not explain your symptom. The instructions in fstab are executed before the network is up. No network, no mount, and it doesn't know how to go back and check.

So one workaround is basically to automate what you have already discovered:

Create a script:
```
gksu gedit /etc/network/if-up.d/fstab
```With this content:
```
#!/bin/sh
mount -a
```Save the file, exit gedit, and back in the terminal make the file executable:
```
sudo chmod +x /etc/network/if-up.d/fstab
```Any script places in if-up.d will be executed only after the network is up.

---

### Post by kamcknig on 2011-06-20
Great!

I will give that a shot, thanks for the explanation!

Kyle

---

### Post by kamcknig on 2011-06-20
This worked, thank you very much!

Kyle

---

