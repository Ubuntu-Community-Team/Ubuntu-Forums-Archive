---
title: "Having Dual-Boot Trouble (3 problems)"
date: 2010-04-04
forum: General Help
---

### Post by CaptainJamie on 2010-04-04
Hello, I was wondering if someone could help me.
Three things are stopping me from installing Linux...

1. When I use it, the wireless doesn't seem to work even when I set up a static IP. Can't figure out much more about the problem. Using a LAN solves this problem but it does mean I have to sit in a corner of my bedroom with my laptop.

2. My family also occasionally use this computer and Linux would scare them so I would like it so you can press the power button and just ignoring everything on the screen Windows 7 will eventually boot.

3.When Windows 7 does boot (and I seem to be the only person with this problem) it says "checking file system on C:\" or something similar and then tinkers with the Linux files and in typical Windows style, ruins everything resulting in Linux and sometimes GRUB not working! After this happened last time I spent a good 8 hours on a live CD backing up my files on a USB and transferring them to my brother's computer then reformatting the hard drive and reinstalling Windows...

So if you can answer any of the above please do because I'm fed up with windows (but need it for itunes!)
Thanks

---

### Post by amite on 2010-04-04
it is general problem with karmic that wireless not working ............for that install bcmwl-kernel-source from syanptic.It will solve ur wireless problem.

---

### Post by amite on 2010-04-04
> **CaptainJamie said:**
> Hello, I was wondering if someone could help me.
Three things are stopping me from installing Linux...



2. My family also occasionally use this computer and Linux would scare them so I would like it so you can press the power button and just ignoring everything on the screen Windows 7 will eventually boot.

So if you can answer any of the above please do because I'm fed up with windows (but need it for itunes!)
Thanks

If u want to switch from ubuntu to windows without reboot u may use virtual box or any other virtual machine.

---

### Post by NightwishFan on 2010-04-04
For Wireless I need to know the model of your card. Also check System -> Administration -> Hardware drivers and tell me what you find there.

For #2, you can modify GRUB to load Windows first. It is fairly simple. I will help you but first tell me if you plan to install Ubuntu using a normal dual boot or WUBI.

#3 I have no idea. How did you install Ubuntu?

---

### Post by CaptainJamie on 2010-04-04
> **NightwishFan said:**
> For Wireless I need to know the model of your card. Also check System -> Administration -> Hardware drivers and tell me what you find there.

For #2, you can modify GRUB to load Windows first. It is fairly simple. I will help you but first tell me if you plan to install Ubuntu using a normal dual boot or WUBI.

#3 I have no idea. How did you install Ubuntu?

OK,

I don't have Ubuntu installed yet. I think I've worked out #2 by looking at another Linux forum. I need to change a 0 to a 2. 
As for Wireless... I have no idea what you mean, "model of your card", but looking at a windows list of drivers that says Atheros AR5007 802.11b/g WiFi Adapter. But I suppose that wouldn't work for Linux... But really I can't tell you because it's not installed yet. Shall I bite the proverbial bullet and install it then post some new details?
#3 Is the biggest problem though. When I installed Ubuntu I just used the live CD and popped it in and clicked install using all recommended settings. Should I get a new distribution as I'm on a laptop?

---

### Post by NightwishFan on 2010-04-04
No, I use Ubuntu on my laptop and I have a Atheros 9k wireless card that works fine. You can feel free to try another distro though. Did you test Ubuntu 9.10 from a live CD yet?

Ubuntu installed normally would not cause issues with Windows boot, so the issue has to be with Windows.

Updating GRUB is more complicated that the forum said, as Ubuntu uses GRUB2. Yes, you have to change a 0 to a 2, but in a different place. It is not difficult though.

---

### Post by CaptainJamie on 2010-04-04
> **NightwishFan said:**
> No, I use Ubuntu on my laptop and I have a Atheros 9k wireless card that works fine. You can feel free to try another distro though. Did you test Ubuntu 9.10 from a live CD yet?

Ubuntu installed normally would not cause issues with Windows boot, so the issue has to be with Windows.

Updating GRUB is more complicated that the forum said, as Ubuntu uses GRUB2. Yes, you have to change a 0 to a 2, but in a different place. It is not difficult though.

Right, I have made a decision, at the moment Windows does not do the checking file system for errors thing. I will install Ubuntu again in a partition and if it goes all weird again I shall know something has gone awry. I shall report back in, oh 30 mins? However long Ubuntu takes to install...

---

### Post by NightwishFan on 2010-04-04
Use the disk tools built into windows to create free space for Ubuntu

---

### Post by CaptainJamie on 2010-04-04
> **NightwishFan said:**
> Use the disk tools built into windows to create free space for Ubuntu

Yes, I have done. 50GB should suffice. Now, I seem to have a problem with my live CD. Must be scratched. It got 90something % then gave me an error. Oh I shall never get it working!
Anyways got to go and see grandma now, I shall try again when I get back.

---

### Post by NightwishFan on 2010-04-04
Ensure you burn the CD at the **slowest speed**, and always check for errors at the boot menu before you attempt an install. This page offers a lot of assistance.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Installing Ubuntu itself is very easy. Please ensure you delete the failed installation before attempting a new one. As for your hardware I would test all of it such as wireless and display from the live CD and only installing if you are satisfied. Some hardware can be made to work post install and wireless is one of these.

I can answer any specific questions you may have when you return. I am glad you gave Ubuntu a try. I have found it to be the most satisfactory operating system out of the many that I have used.

Good luck, and when you return I am sure we can get it working.

---

### Post by CaptainJamie on 2010-04-04
> **NightwishFan said:**
> Ensure you burn the CD at the **slowest speed**, and always check for errors at the boot menu before you attempt an install. This page offers a lot of assistance.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Installing Ubuntu itself is very easy. Please ensure you delete the failed installation before attempting a new one. As for your hardware I would test all of it such as wireless and display from the live CD and only installing if you are satisfied. Some hardware can be made to work post install and wireless is one of these.

I can answer any specific questions you may have when you return. I am glad you gave Ubuntu a try. I have found it to be the most satisfactory operating system out of the many that I have used.

Good luck, and when you return I am sure we can get it working.

OK thanks. It is that it's scratched though because it's quite old now and I've used it a few times before. Now I'm out of blank CDs. Anyone know how to boot from a USB? Can I just extract the .iso onto a USB stick? I'll try that now... Hmm, where did I put him last?

---

### Post by NightwishFan on 2010-04-04
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

This program runs on Windows I believe it will let you make a live USB. Any questions feel free to ask.

---

### Post by CaptainJamie on 2010-04-04
Well. I really must say, thank you very much for all your help. You've been very helpful I must say. Anyway I seem to have solved the problem (#3 I think) of windows messing stuff up you've just got to let it do things at first then when it asks if you want it to repair (lol) say no thank you, ignorant Windows... Anyway still having trouble with wireless, if you could outline a solution I would be grateful. Oh and some detail about making Windows (grr) default, would be nice but as I say, you've been a great help anyway so don't feel the need to reply if you can't be bothered.
Thanks again,
Jamie

Oh scratch that bit about wireless... I put in the same numbers I have been putting in for days and suddenly they start to work... 1 problem remains, who will solve it?

---

### Post by NightwishFan on 2010-04-04
It is no problem. Firstly, I shall outline the wireless issue. Check System -> Administration -> Hardware Drivers. If there are no drivers available do the following. Open Applications -> Accessories -> Terminal. Type the following command exactly, and push enter. You will be prompted for your password. _It will not show up when you type it, that is normal._
```
sudo lshw -C network
```

Post the output here. Surround it with a code tag (the # symbol near the end of the tool bar)


For the booting issue, please do the following:

[LIST=1]
[*]Press alt+f2, a box should come up. Type this and then hit Run: ```
gksudo gedit /etc/default/grub
```
[*]A text file should open. One of the top lines says "GRUB_DEFAULT=0" Change that to "GRUB_DEFAULT=2". Save the file, and close it.
[*]Open up Applications -> Accessories -> Terminal. Type the following and push enter. You will need to enter your password. ```
sudo update-grub
```
[*]Reboot, and see if Windows boots first.
[/LIST]

Happy to help, welcome to the Ubuntu community. You might find these pages useful.
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)
[http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by oldfred on 2010-04-04
Some windows  software writes hidden info into the MBR. New grub is slightly bigger than the windows boot loader or old grub and can get corrupted by this.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
HP ProtectTools, Dell Recovery, and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct issues with MBR
[http://ubuntuforums.org/showthread.php?t=923576](http://ubuntuforums.org/showthread.php?t=923576)

---

