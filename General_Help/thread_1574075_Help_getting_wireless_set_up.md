---
title: "Help getting wireless set up"
date: 2010-09-13
forum: General Help
---

### Post by pokeman89 on 2010-09-13
I have used ubuntu once for about a day and a half and decided to give it a try again since I got a new laptop. I downloaded Ubuntu Studio but couldn't get connected to the internet, or even figure out what info it wanted to connect. I read a forum post about it and read that installing ubuntu first and then updating the installation to Studio *(EDIT: Causes login errors, not an option), so I tried wiping that and Although there is a wireless status indicator at the top, it says device not ready. I assume I need a driver or firmware or something, but I'm not sure. Can anyone help me walk through this? I am still not used to the terminal, though I am slowly learning. Right now I'm using the internet on the same laptop but on the windows 7 OS partition. I also have an IBM ThinkPad running XP for quick transfer via flash drive.
 
Laptop specs:
 
Dell Inspiron 1545, all stock with the exception of the 9 cell battery and Radeon HD 4330. Some sort of Broadcom Wireless chip. Windows 7 with a 10GB partition for Ubuntu Studio 10.04
 
Note: 64-bit.
 
The included help files are useless. It tells me to click on the network manager on the top bar which is nonexistent. And the wireless thing is disabled according to ifconfig... but the only solution is a hardware switch that my laptop doesn't have. I tried toggling the wifi on and off in windows with no help either.

---

### Post by pokeman89 on 2010-09-14
I tried working with it all night to no avail. In fact, the only thing I did manage to do was screw up the entire installation to the point where I couldn't log in. I could really use some help, I'm totally new to using the terminal and obviously it shows when I try without knowing what I am doing. Currently I have the Ubuntu Studio 10.04 on. I tried getting drivers and got two available ones, Broadcom B43 and Broadcom STA, however each time I tried to activate them it asked me to mount the installation CD evne though it already is, and it eventually fails. No ethernet, no Wireless, all I have to transfer files is a flash drive and an old IBM ThinkPad running XP.
 
Can you help a clueless guy like me? :D

---

### Post by pokeman89 on 2010-09-14
Can anyone help me? I promise I'm a person who can follow instructions O:)

---

### Post by stinkeye on 2010-09-15
UbuntuStudio does not come with network manager installed because it can interfere with recording.

You can install it by going to the ubuntu studio cd and installing all the packages
in **/pool/main/n/network-manager**
Just double click on the file and if it fails, take a note of the dependency needed and install that file first.

Then install network-manager-gnome in **/pool/main/n/network-manager-applet**
I can't remember now but I think I had to install another package to do with policykit.

But if your fairly knew to ubuntu and are having trouble getting your network up,
it may be better to install normal Ubuntu and then install any sound or video programs you want to try.

Ubuntu studio just gives you a better environment for doing professional
quality recording, video editing, etc.

---

### Post by pokeman89 on 2010-09-15
Thank you for the reply, I was beginning to wonder if I would get any help at all.

I did not know about the whole network manager thing, so I installed regular Ubuntu 10.04 to clear that up seeing as most of the software in studio is available to use in Ubuntu (I hope?). I still cannot connect to the internet however, Ethernet or wireless. I get the "device not ready" message. I tried fetching drivers but it failed seeing as there's no connection to the internet. It identified both the broadcom 43 and broadcom sta. Drivers so I assume one is wireless and one is Ethernet. How do I get them and install them without a connection?

---

### Post by stinkeye on 2010-09-15
Trouble shooting network issues is beyond my skill.
What's available is constantly changing.
I suggest you post in this section for help.
[**_[COLOR="DarkRed"]http://ubuntuforums.org/forumdisplay.php?f=336[/COLOR]_**]("http://ubuntuforums.org/forumdisplay.php?f=336")

---

### Post by pokeman89 on 2010-09-15
> **stinkeye said:**
> Trouble shooting network issues is beyond my skill.
What's available is constantly changing.
I suggest you post in this section for help.
[**_[COLOR=DarkRed]http://ubuntuforums.org/forumdisplay.php?f=336[/COLOR]_**]("http://ubuntuforums.org/forumdisplay.php?f=336")


Ok, thanks for the information and I appreciate the advice :)

---

### Post by Iowan on 2010-09-15
Closed. Discussion moved to:
[http://ubuntuforums.org/showthread.php?t=1575197]("http://ubuntuforums.org/showthread.php?t=1575197")

---

