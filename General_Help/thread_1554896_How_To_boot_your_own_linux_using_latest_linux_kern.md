---
title: "How To boot your own linux using latest linux kernel and grub form cd or usb"
date: 2010-08-17
forum: General Help
---

### Post by Vipul Gupta on 2010-08-17
[FONT=Verdana]Hey!!!...I want to know how to use a grub with a compiled kernel...and perform the boot of the system using a Cd-ROM for this purpose...[/FONT]
Plz help me out...

thanx in advance...

---

### Post by oldfred on 2010-08-17
This may help:

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM")

I prefer to use USB flash drives, now. But your system has to boot from a USB drive. It is easy to install grub2 to a flash drive and edit its grub.cfg to boot just about anything you want to boot. Getting the boot commands correct is the biggest issue and yours will have to be totally customized for your kernel.

---

### Post by Vipul Gupta on 2010-08-19
Thanx....this link gave me lot of help.....I am able to make my own usb grub rescue and it is only for my pc.But i wan to knw if there is no operating system then how to perfom the boot using grub.Actually i want a universal boot i.e it can run on any pc having no os.
Also i hav latest linux kernel sources and compiled them. Now wat i want is to use tht universal grub boot  and tht compiled kernel toghter and run my pc and i want to knw tht if this can be done or not. 

Plz help me  figuring out this..
thanx in advance...

---

### Post by oldfred on 2010-08-19
I have two flash drives set up as emergency boot. One I also use for my installs. Grub can be seen as a mini operating system that boots but has very few commands, most just to boot another system.

The 4GB uses grub2 to boot and loop mounts ISO files. I have Ubuntu, gparted, system rescue and several others plus a little space for scripts and other info.

 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
[http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/](http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/)
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

The 16GB has a full install of Ubuntu. I could put some of the ISO here also and may soon.

Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html]("http://members.iinet.net/%7Eherman546/p19.html")

---

### Post by Nick_Jinn on 2010-08-19
I feel like this is branching off into too many directions, even time I click on a link.
 
 
Is there a simple 'how to' wiki page that will tell me how to install Linux to a USB, but where it will get it to behave like a hard drive isntall rather than a 'live image' that wont allow me to install updates or upgrade to the next release or do certain things that require root privileges?

---

### Post by oldfred on 2010-08-19
Nick_Jinn

Did you look at the link to Herman's page. Very detailed as Herman always is. He also has another page on dual boot to two drives which is closer to what I did to install to my 16GB flash drive.

---

### Post by Nick_Jinn on 2010-08-19
I read the first page. It wasnt very helpful. It was talking about USB3 and how things will improve.
 
Is there a page on that site I should be looking at?
 
 
I dont really care about dual boot at this point. I am trying to get my usb to behave like a regular install instead of a live image.

---

### Post by oldfred on 2010-08-19
Herman has a lot of detail but it is a full install. See the entire install that he does.

---

### Post by Nick_Jinn on 2010-08-19
I think maybe you linked me to the wrong page?
 
If I scroll down I see a list of external links. Should I be following one of those? The one that talks about dual booting?

---

### Post by oldfred on 2010-08-19
When I click on it I get p19 the Flash or SSD encrypted install.

Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)

---

### Post by Nick_Jinn on 2010-08-19
I found it. It originally wanst loading the whole page.....Man, that guy knows how to take something simple and make it long and complicated with pictures and explainations that are not required for the next step, by the dozen. Its not 'difficult' some much as tedious to read through. 
 
 
I was hoping for a purely GUI method of getting my flash drive to boot linux, even if it required using the bios to load on a computer that doesnt already have grub. That didnt work out since the bios loader boots me into a black screen when I select my USB device with linux installed normally. I dont quite feel comforatble using the command line for this yet. I was really hoping there was a simple way of getting it to boot, just like a live image, but then it behaves like a real installation instead of a live image.

---

