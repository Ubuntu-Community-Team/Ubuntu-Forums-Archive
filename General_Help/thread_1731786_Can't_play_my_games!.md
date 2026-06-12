---
title: "Can't play my games!"
date: 2011-04-17
forum: General Help
---

### Post by ANTlabs on 2011-04-17
I switched over to ubuntu a month ago and have had a fairly easy time setting things up, Until I got to my games...

 So, here is a list of things I've tried:

Wine
V-box
Using windows on an old computer (no video or sound cards, very slow)
Running windows from a USB hdd
Running windows from  a flash drive
And a lot more...

Now, I think the best way to get it running is by putting windows on my real hdd. But if I do, it'll wipe my ubuntu. Is there any way to make a dual boot after ubuntu is already installed? (no backup drive is available at the moment)

---

### Post by PCaddicted on 2011-04-17
You mean Windows games?But what games?Please note that Wine cannot run all Windows applications,only a selection of them.However,beware that it represents a security hole,as some Windows viruses might take advantage of it to infect your Linux PC,according to Wikipedia.Regarding VirtualBox,I do not think playing games on a virtual machine is a good idea,because the performance is reduced,as the host machine has to share RAM memory with the virtual machine,and it is recommended for the latter to have less than 50% of the RAM available on the system.
Also,I know from my own experience that an OS run from an external boot device(an USB stick or a LiveCD) will boot and perform more slowly than an operating system that is installed on the computer.
Yes,it is possible to make a dual boot where one of the OSs is Ubuntu but I think you'll have to reinstall Ubuntu for this.When the computer boots from the Ubuntu LiveCD,you'll have 2 options:Try Ubuntu and Install Ubuntu.Regarding the latter,under the Install Ubuntu button it's written with small letters something like this:"Install Ubuntu alongside other operating systems or as your only OS".
Remember that I am not a pro so my advice might not be complete or totally correct.Hope it helps you,anyway.

---

### Post by flipper T on 2011-04-17
back up your files

install windows (overwriting ubuntu)

install ubuntu as a dual boot

should take you about 60 minutes

---

### Post by mastablasta on 2011-04-17
yes it's possible to install windows after ubuntu. what basiucally you need to do is dedicate a piece of hard disk for windows. Install windows there and then you will need to restore GRUB

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by crazyguy510 on 2011-04-17
I would do what was suggested above. While Ubuntu is an excellent OS, running windows applications on it perfectly has been so far an impossible task.

However, some games do seem to work. If you have your heart set on Ubuntu as your primary OS, then check out [http://appdb.winehq.org/](http://appdb.winehq.org/) and search for the game your trying to run. If someone's gotten it to work then it'll say how well and what you may need to do to install it. :D

---

