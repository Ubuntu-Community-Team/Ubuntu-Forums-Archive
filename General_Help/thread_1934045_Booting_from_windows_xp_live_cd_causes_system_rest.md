---
title: "Booting from windows xp live cd causes system restart"
date: 2012-03-01
forum: General Help
---

### Post by x5pyd3rx on 2012-03-01
I am trying to create a windows xp partition on my laptop. 

I downloaded xp sp3 from msdna website (what a hassle) , and have a .iso file. I have tried it on two separate dvd's however each time the pc boots it prompts me with  

"press any key to boot from cd..." i press a key the screen goes black and the laptop simply restarts repeating the process until i give up and let it boot from grub.

If you need me to try any commands and give you output let me know.

Thank you in advance for any help you can offer.

---

### Post by dino99 on 2012-03-01
As you might know here is ubuntu's home. Using virtual subsystem like virtualbox or vmware let you use your exe progs, so no need of old crap.

[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

---

### Post by imachavel on 2012-03-01
not bad, no need to partition a new spot on the Hdd. just download virtual box ose, and going to virtualbox.org is a good way to visit their help forums and ask questions. you configure each virtual device in settings, select the location of the OS you want to install. I actually have an account there, and hope I didn't forget my log in. But I am very very low on virtual knowledge. You will need a separate usb filter for each usb device you want to use. Problem is virtual machines use up a lot of shared memory. What model computer/laptop do you have? What type of processor? Do you know what it's clocked at? What brand? What type of architecture?

If virtual box with good ram assigned slows down on you, then you might want to re partition the drive, and install windows to one partition. Download gparted .iso and burn it to a disk. What I'm wondering, if your hdd is booting up(because you are on an OS right now), but you can't boot to your windows cd,(btw you can't boot to windows live cd, only boot to windows cd to install, repair, or access repair console), then maybe your windows cd isn't working. If you put your windows cd in the drive once OS on main partition on grub is loaded, what does it show if you access the cd?(btw what are you using for grub? Windows grub? Or grub2 or linux legacy grub?)

is your cd drive working? Have you tried using a different cd in the cd drive to see if it works? Are you trying to repair a previous dual boot? If so have you looked into boot repair developed by the linux team?

Oh wait I didn't read your thread that carefully. Ok you downloaded windows xp service pack 3 and installed it to two cds. Neither will boot. Wow winblows. That sucks you payed for a one time activated windows .iso and burned it to a cd twice, and it won't work? Any reason why you can't just skip using windows? Have you tried booting the windows cd in another computer to see if it boots? Really sorry, that really sucks, brand new fresh windows cd and you can't boot to it. 

Why don't you call up microsoft support and see if they can walk you through troubleshooting??

---

### Post by MARP1961 on 2012-03-01
Your Windows XP iso needs to be turned into a** bootable** CD or DVD by burning the iso file as an** image**. Make sure you haven't just burnt a** data disk**. Are you sure you have created a proper bootable disk?

If you do this and the install starts, please be aware that you will not be able to activate your Windows or get any updates unless you have used an **identical** version to the one you have a Window Product Number for. If your Product Number sticker is for Windows XP Home OEM then you must have an iso for Windows XP Home OEM.

Another thing to remember is that if you install Windows **after** Ubuntu then the GRUB bootloader will be overwritten by Windows and you will not be able to boot into any Ubuntu partitions you may have kept. You can restore the Grub bootloader afterwards and there is information on how to do this on these forums.

---

### Post by imachavel on 2012-03-01
true. If possible, download gparted .iso and burn it to a disk with iso burner, not regular burner. I've never tried burning an .iso file to a cd that didn't burn it as an image, so wasn't sure if it was possible. But if you want to repartition your drive with gparted, or not repartition, but create a new partition in empty space, give it a shot. Hence why I was asking what model of computer/how large of a drive do you have installed. 

yes OEM sucks, OEM means usually one time activation, as given by the factory which is default. You'll know as the sticker on the side of your tower for your model of pc will read the activation key. If it's home version, then you might be able to reuse the activation key, but there is no guarantee. Professional will definitively not let you reactivate. If you need to reactivate, and don't have a new activation key, if you have the exact same windows cd OS version, and you install and it doesn't let you use the same activation key, you might be able to call up Microsoft support and ask for a new activation key if you don't tell them you re burned the exact same OS from a site online, tell them it's the same disk. Essentially it will be THE EXACT SAME DISK, but expecting a different activation. I don't see how this would be wrong. I was under the impression however, that you paid for a brand new activation key.

---

### Post by MARP1961 on 2012-03-01
You **can** reinstall both Windows XP Home and XP Professional OEM as long as you have a Windows disk for **exactly the same version**.

I believe obtaining a copy by download is against the terms of Microsoft's license but** it will work.** 

Most computers are sold with Windows preinstalled. If there is a manufacturer's sticker with Windows then it will be OEM.

---

