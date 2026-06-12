---
title: "Booting Windows 7 computer from ubuntu thumb drive"
date: 2012-06-08
forum: General Help
---

### Post by TRG1 on 2012-06-08
I have created a bootable usb thumb drive using unetbootin. The computer will boot from the thumb drive only if I disconnect the c: drive. I have set the bios with the removable device as the primary and disconnected all other usb devices while trying to do this. Nothing works. I am able to boot from the thumb drive with the c: drive connected if the thumb drive is a Windows install drive. 

Any suggestions?

---

### Post by Mark Phelps on 2012-06-08
When only the USB is connected, the PC boots from that because that is the only device containing boot code.

IF it doesn't boot from that when your Windows hard drive is connected, that's because it finds the boot code in the hard drive BEFORE it looks at the USB.

You will have to experiment with your BIOS boot default settings to see which one will select the USB first, when the Windows hard drive is connected.

That varies by PC.  On one PC, I had to set the BIOS to boot from the second floppy drive -- because the BIOS thought the thumb drive was a floppy drive!

---

### Post by TRG1 on 2012-06-08
> **Mark Phelps said:**
> When only the USB is connected, the PC boots from that because that is the only device containing boot code.

IF it doesn't boot from that when your Windows hard drive is connected, that's because it finds the boot code in the hard drive BEFORE it looks at the USB.

You will have to experiment with your BIOS boot default settings to see which one will select the USB first, when the Windows hard drive is connected.

That varies by PC.  On one PC, I had to set the BIOS to boot from the second floppy drive -- because the BIOS thought the thumb drive was a floppy drive!

I have tried all the boot configurations and it doesn't ever go to the thumb drive. However, it had no trouble booting from a thumb drive with Windows install on it. Must be something else, eh?

---

### Post by Kr0nZ on 2012-06-08
> **TRG1 said:**
> The computer will boot from the thumb drive only if I disconnect the c: drive.

You need to set the boot priority to boot from usb before the harddrive, but this is where you need to do a little investigative work, because the USB stick could be detected as anything, on my pc my thumb stick is detected as an hard drive, but that same thumb drive is detected as a cdrom on a different PC.

Another way to boot, is when you first turn on your PC and you get the text at the beginning (the post), on most PCs their should be an option to select 'boot device', usually F10 or F12.

---

### Post by wilee-nilee on 2012-06-08
What is it that you are actually trying to do what is the final goal here?

---

### Post by TRG1 on 2012-06-08
> **wilee-nilee said:**
> What is it that you are actually trying to do what is the final goal here?

I run my computers without av software and I don't want to install the usual type of av program. It is my impression that I can run a virus check from a ubuntu thumb drive, so this was just my first step to see if I can get the thumb drive to boot. 

I have tried every available configuration of boot device order, but it never boots from thumb drive with the windows drive connected. However, I know it will boot from the thumb drive with the c: drive connected if the thumb drive has windows install on it. I have two thumb drives, both 8gb SanDisk. One is set up with Windows install, and the other with ubuntu. I removed everything that came with the drives when I bought them.

---

### Post by wilee-nilee on 2012-06-08
> **TRG1 said:**
> I run my computers without av software and I don't want to install the usual type of av program. It is my impression that I can run a virus check from a ubuntu thumb drive, so this was just my first step to see if I can get the thumb drive to boot. 

I have tried every available configuration of boot device order, but it never boots from thumb drive with the windows drive connected. However, I know it will boot from the thumb drive with the c: drive connected if the thumb drive has windows install on it. I have two thumb drives, both 8gb SanDisk. One is set up with Windows install, and the other with ubuntu. I removed everything that came with the drives when I bought them.

Even if you ran every av that is possible from Linux it still would not cover what should be covered that is bad reasoning.

You can use supergrub loaded to the thumb to boot widows.

Your reasoning is a bit off here.

Running a windows set up without a av is not really advised, no legitimate IT person would advise this, or run their own set up this way, if you are going on the web with it.

---

### Post by TRG1 on 2012-06-08
> **wilee-nilee said:**
> Even if you ran every av that is possible from Linux it still would not cover what should be covered that is bad reasoning.

You can use supergrub loaded to the thumb to boot widows.

Your reasoning is a bit off here.

Running a windows set up without a av is not really advised, no legitimate IT person would advise this, or run their own set up this way, if you are going on the web with it.

I have some computers that are never have a browser opened nor are they used for email. The only computer I use for such things has av on it. Nevertheless, I would like the ability to scan these computers from an external drive without installing any software. I would not expect anyone to agree with this approach, but it's what I'm trying to do. It is not critical since I've been running these computers without av for years.

---

### Post by wilee-nilee on 2012-06-08
> **TRG1 said:**
> I have some computers that are never have a browser opened nor are they used for email. The only computer I use for such things has av on it. Nevertheless, I would like the ability to scan these computers from an external drive without installing any software. I would not expect anyone to agree with this approach, but it's what I'm trying to do. It is not critical since I've been running these computers without av for years.

Cool just wanted to make sure you understand, an av needs to be updated though, and there are better live cd's that can be run for a windows setup then any offered in a unice set up.

The ones run from linux are just the windows versions of ones already offered on live cd's anyway.

[http://www.techmixer.com/free-bootable-antivirus-rescue-cds-download-list/](http://www.techmixer.com/free-bootable-antivirus-rescue-cds-download-list/)

It sounds like what you need is a full install of a linux on the thumb, that way you can update the av, then boot it on the windows se tup and scan it I guess.

---

### Post by TRG1 on 2012-06-08
> **wilee-nilee said:**
> Cool just wanted to make sure you understand, an av needs to be updated though, and there are better live cd's that can be run for a windows setup then any offered in a unice set up.

The ones run from linux are just the windows versions of ones already offered on live cd's anyway.

[http://www.techmixer.com/free-bootable-antivirus-rescue-cds-download-list/](http://www.techmixer.com/free-bootable-antivirus-rescue-cds-download-list/)

It sounds like what you need is a full install of a linux on the thumb, that way you can update the av, then boot it on the windows se tup and scan it I guess.

I did another installation of ubuntu on the thumb drive and it still would not boot, so on a hunch I switched out the normal c: drive which is an SSD to an earlier drive which is HDD. The thumb drive boots ok in this instance, so I guess the SSD is somehow beating the thumb drive to the punch. So I'm giving up on this and going to try the Kaspersky rescue disk approach or something similar.

---

### Post by wilee-nilee on 2012-06-08
> **TRG1 said:**
> I did another installation of ubuntu on the thumb drive and it still would not boot, so on a hunch I switched out the normal c: drive which is an SSD to an earlier drive which is HDD. The thumb drive boots ok in this instance, so I guess the SSD is somehow beating the thumb drive to the punch. So I'm giving up on this and going to try the Kaspersky rescue disk approach or something similar.

You might just need to use the per session key  boot prompt to boot the thumb. Mine is f12 used as if you are going to the bios at powering on. Usually this info is easily found on the web with a search using the computer model and one time boot or a similar reference. This info may be in a manual; as well.

---

### Post by TRG1 on 2012-06-08
> **wilee-nilee said:**
> You might just need to use the per session key  boot prompt to boot the thumb. Mine is f12 used as if you are going to the bios at powering on. Usually this info is easily found on the web with a search using the computer model and one time boot or a similar reference. This info may be in a manual; as well.

Yes, thanks, that did the trick. I've never been in the habit of doing that to select boot device and since I use synergy, I have a little miniature keyboard I use just to start synergy, but it doesn't have function keys, so I had to drag an old keyboard out from storage. Oh well...

---

### Post by wilee-nilee on 2012-06-08
> **TRG1 said:**
> Yes, thanks, that did the trick. I've never been in the habit of doing that to select boot device and since I use synergy, I have a little miniature keyboard I use just to start synergy, but it doesn't have function keys, so I had to drag an old keyboard out from storage. Oh well...

Hehe the hard work we do. ;)

---

