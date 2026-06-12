---
title: "Sata HDD Install Problem"
date: 2010-04-28
forum: General Help
---

### Post by Irishbmx on 2010-04-28
Hello I've been trying to investigate this online as much as I can and it seems many other people have the same problem that use my board but I can't find a fix.
The board is and XFX GeForce 8200 AMD SOCKET 940 DDR2, basically the problem is linux no matter what version I try won't see the HD.
I've tryd to hit the quit button on the install and look for the hd inside live CD on sata mode achp mode and DID for linux none of which work.

I contacted xfx and they said this **"As of ubuntu 8.10 there was a way to get this board working. If I remember correctly you need to use the `pci=nomsi` on the grub startup command, then you have to set the other options (F6) have both noapic and nolapic check, also using (F4) set the install to safe graphics. If thats done that and have the latest BIOS people were able to get this board working in the past, its been some time since its come up though."**
I Couldn't figure out how to do this really I did manage at one point to get into the grub line but  am confused on how to do this.
Any help is appreciated and the more detailed you can be the better I am not an expert.

Also to add I am trying to install ubuntu 9.10 32 bit and I also have an 8.04 disk as well as mandrive 2010 with knoppix 6.3 on the other side.

---

### Post by Sin@Sin-Sacrifice on 2010-04-28
[This]("https://help.ubuntu.com/community/BootOptions") will show you how to add boot flags but I have the same chipset and haven't had that problem since hardy. Weird...

---

### Post by Irishbmx on 2010-04-28
> **Sin@Sin-Sacrifice said:**
> [This]("https://help.ubuntu.com/community/BootOptions") will show you how to add boot flags but I have the same chipset and haven't had that problem since hardy. Weird...

Thanx, hmm yea that is odd might be because I ran hardy on IDE and never messed with anything sata on my board until now. did you have to edit anything in grub when you first installed hardy?

---

### Post by Sin@Sin-Sacrifice on 2010-04-28
Yep... had to use the pci=nomsi flag to boot or it wouldn't see the SATA drives. I haven't had to do that for a long time now though. A fresh install of karmic had no problem seeing my drives. Although I did do a BIOS update before hand so that might be why. Check to see if XFX has an update for your board. If it's the 750a like mine then I know they do.

---

### Post by Irishbmx on 2010-04-28
Ok I got it to install, now when it trys to boot from the HD it says Gave up waiting for root device.
I have the sata set to the ach with DID for linux, do I need to switch it back to SATA mode or ... I dunno any Ideas? Thanx a bunch for the help btw making good progress :)

---

### Post by Irishbmx on 2010-04-28
been trying all kinds of things, found a post that said something about adding root=/dev/sda1 to the thing as well as the pci=nomsi
Not having any luck about to start banging my head on a wall I just keep getting the **"Gave up waiting for root device"** message

---

### Post by oldfred on 2010-04-28
Not familiar with your motherboard. I have seen where the drives have to be set to IDE or possibly other settings. I would try different settings in BIOS and see if that makes any difference. 

Also is your BIOS up to date. Sometimes they have newer versions even for a brand new board.

I changed one setting in my BIOS and Ubuntu worked just great but XP would not boot. So it depends on the BIOS settings.

---

### Post by Irishbmx on 2010-04-28
Tryd all bios settings, But good news is I got it to boot I edited out the root=ucsi 86758687 something like that changed it to root=/dev/sda1 and added msi=nopci got it to boot onto the HD and the install seemed to have gone smooth.

But now my problem is lol
[B]-"pci=nomsi" in the boot screen after pressing "e".
-Then when I ran "gksudo gedit /etc/default/grub" in a terminal I changed "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"" to look like "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=nomsi""
-I then saved that file before closing it then "sudo update-grub"[/B]
I did this then rebooted so I wouldn't have to enter the pci=nomsi thing everytime and I got a grub error on startup, didn't wright it down but it said something like file system does not exist and popped up a grub rescue thing that looked like a cammond prompt but did nothing I knew how to do.
So I am reinstalling again going to fallow all the same steps any Idea what I did wrong in the grub?

---

### Post by oldfred on 2010-04-29
I do not think the changes you made were the problem but you need to make the boot not use UUID (for whatever reason?) as you initially did.

Was the error message anything like one of these, with suggested solutions:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Main_Page)

---

### Post by Irishbmx on 2010-04-29
> **oldfred said:**
> I do not think the changes you made were the problem but you need to make the boot not use UUID (for whatever reason?) as you initially did.

Was the error message anything like one of these, with suggested solutions:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Main_Page)
Hmm not sure if what I did this time was the right way but now everything works.
I edited the grub just like last time only this time I did the permanent edit on the root= so instead of the uui thing it's root=/dev/sda1

So now it boots straight into linux without any problems or hangups :)
TY for the comment on the UUI I wouldn't have though of that.

---

### Post by oldfred on 2010-04-29
Glad you got it working.

UUID's are supposed to be the better way as they are less likely to change. Any partition changes may change your sda setttings and cause issues. Only deleting should change UUIDs so they are preferred. But we have seen several places where they do not work.

---

