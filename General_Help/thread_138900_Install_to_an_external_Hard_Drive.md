---
title: "Install to an external Hard Drive?"
date: 2006-03-02
forum: General Help
---

### Post by Madman68 on 2006-03-02
Just wanted to ask if it is possible to install Ubuntu to an external usb hard drive. I have a Western Digital 40GB hard drive, I also have a larger one but I would have to clean it out. Thanks!

---

### Post by SectionThree on 2006-03-02
Sorry Charlie, but you can't boot up from USB devices. It's not allowed. Get yourself a firewire drive, then you're in business (likewise, if you have the old SCSI ports on your computer, you can boot up from a SCSI drive).

If you're tying to circumvent the need to partition your internal drive for a dual-boot scheme, don't worry, it's not as daunting as it sounds. Just copy all your data to your USB external and you'll have it available for when you reinstall your other OS.

I don't know what kind of machine you have, but what I've got going right now is a ppc running both Ubuntu and OS X.  When I did the same thing I just suggested to you, I just copied all my applications back to my OS X boot partition and they all worked just fine-- I didn't need to re-install them or anything like that.

---

### Post by Elvish Legion on 2006-03-02
[QUOTE=SectionThree]Sorry Charlie, but you can't boot up from USB devices. It's not allowed. Get yourself a firewire drive, then you're in business (likewise, if you have the old SCSI ports on your computer, you can boot up from a SCSI drive).

If you're tying to circumvent the need to partition your internal drive for a dual-boot scheme, don't worry, it's not as daunting as it sounds. Just copy all your data to your USB external and you'll have it available for when you reinstall your other OS.

I don't know what kind of machine you have, but what I've got going right now is a ppc running both Ubuntu and OS X.  When I did the same thing I just suggested to you, I just copied all my applications back to my OS X boot partition and they all worked just fine-- I didn't need to re-install them or anything like that.[/QUOTE]


Then what do you call [http://www.tomshardware.com/2005/11/10/taking_linux_on_the_road_with_ubuntu/page2.html]("http://www.tomshardware.com/2005/11/10/taking_linux_on_the_road_with_ubuntu/page2.html")

---

### Post by akiro.yamamoto on 2006-03-02
Yup it seems possible. 
However the computer you hook it up to will have to be able 
to boot from a USB drive, I don't know how many systems support this feature. If not
no joy. So maybe the live CD with an attatched USB drive for storage would be a 
better configuration, since most modern PCs support booting from the CD drive.

---

### Post by professor_chaos on 2006-03-03
modern systems should boot to usb.
check your bios and see.

---

### Post by cotcot on 2006-03-03
It is possible although difficult. I tried it myself but quit although my BIOS supports USB HDD. It was easier to install dual boot on the internal HDD with grub bootloader on floppy. 
There is another thread about it in this forum : [http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)
There is also this howto : [http://frontier05.blogspot.com/2006/01/installing-ubuntu-to-external-usb.html](http://frontier05.blogspot.com/2006/01/installing-ubuntu-to-external-usb.html)

---

### Post by SectionThree on 2006-03-03
[quote=Elvish Legion]Then what do you call [http://www.tomshardware.com/2005/11/10/taking_linux_on_the_road_with_ubuntu/page2.html]("http://www.tomshardware.com/2005/11/10/taking_linux_on_the_road_with_ubuntu/page2.html")[/quote] 
I will now eat my words. Got any salt?

---

