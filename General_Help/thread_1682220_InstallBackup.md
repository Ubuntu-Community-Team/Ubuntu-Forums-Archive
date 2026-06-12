---
title: "Install/Backup"
date: 2011-02-05
forum: General Help
---

### Post by Donjr on 2011-02-05
I am new to Ubuntu and very impressed with it. My questions are as follows.
1st, I like to Distro hop and try all the different flavors, What i wanted was HOW do i back up my original install of Ubuntu 10.10 and try different like Natty and then (screw it up) uninstall it and go back to my original. Every time i try this i screw up the grub somehow. I have Installed Ubuntu on a Hd with the following partitions  8gb swap,40gb root, 12gb boot and 100gb home
This is a new comp Dell 537 with 4 GB ram Nvidia 8400GPU.
It seems every time i try anything Natty that my video does not wor. I have googled many many different explanations and none seem to work without Re-installing new.
2Nd question is a little easier. I am looking for what you think would be the best info source on Conky.  TYAVMIA :-)

---

### Post by techunit on 2011-02-05
What are you trying to accompish. You do not install alphas when you have little experience with Ubuntu. Ok you have been scolded lets try to fix it.
Now I can't stay on here all day I have a meeting in fifteen minutes so I'm going to point you toward possible problems you can look at.

You have what looks like 4 primary partitions this is a limit! you can't have any more period.

You should probably do a clean install because it sounds like you really mucked up your home partition.

The next time you want to try natty do it in a virtual machine like virtualbox.

Please don't install alphas on end machines! Bad idea!

---

### Post by kn0w-b1nary on 2011-02-05
You can do complete backups w/ remastersys
[http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)

Hope this helps!

---

### Post by Donjr on 2011-02-05
Not sure if this is where i reply to my own questions?
What i am trying to do is just learn different things and i have started here. As far as installing, the tower i am using to install different distros is a guinea pig so to speak. I have my regular comp running fine with Ubunt 10.10 and dont mess with anything on it as it is my daily comp. I just like to tinker and it seems the best way for me to learn is to BREAK stuff  :-)
I dont care if i have to do things over and over was just looking for a way to mess it up and easily fix it.
And thank you for the link on backing up . I will be looking into that also.
TYAVMIA  :-)

---

### Post by mike555 on 2011-02-05
You might want to do what I do on my test machine ..... I install and have it install grub to the partition I'm installing to (not the mbr) then use a different boot loader to go to each partition and it's grub........ (I use "Gag bootloader" ...   [http://gag.sourceforge.net/](http://gag.sourceforge.net/) )... that way when you install a new operating system over an old one it doesn't mess up the main bootloader.

---

### Post by techunit on 2011-02-05
I agree with mike555 a chainboot might be what you need

Ok that makes sense to use a testbed. I thought you were just another noobie who didn't know what they had done and went and gone and trashed their computer.

Obviously this is not the case and I didn't give you enough credit. I sometimes forget my philosophy that beans mean nothing when you have only just discovered the forum.

Good Luck.

---

