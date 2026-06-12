---
title: "iso image to usb stick?"
date: 2010-01-12
forum: General Help
---

### Post by jakeeee on 2010-01-12
Hi, I have a netbook with no cd drive.
And I've been trying to dual boot Ubuntu and Win7 for days now.
I cant boot off my usb stick for some reason.
Here's the command i used: sudo dd if=/where/the/iso/is/located.iso of=/dev/sdb1

Is that correct?
Does that make it bootable?

Is there a GUI for this?

---

### Post by Linuxforall on 2010-01-12
In Ubuntu system>administrator>usb starup disk creator 

Very simple and easy to do. Make sure you have the CD or ISO ready.

---

### Post by plusnplus on 2010-01-13
Hi jakeeee,
"In Ubuntu system>administrator>usb starup disk creator " is only available in latest ubuntu version.

try google: pendrivelinux.com

---

### Post by jakeeee on 2010-01-13
I have tryed using that.
When I select my iso it doesnt do anything.
When I click format under disk to use, it wont do anything.
Any other options?

And btw, I am currently using 9.10

---

### Post by jakeeee on 2010-01-13
Ohh! and im trying to get win7 installer to boot off the usb.
Not ubuntu. I already have ubuntu haha.
Sorry i should have mentioned that before

---

### Post by sigmarhophi on 2010-01-13
I have a net book with no cd.  I am now running 9.10 remix by using the bootable USB instructions as found here:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

worked like a champ!

---

### Post by garvinrick4 on 2010-01-13
If USB startup disc creator stays shaded and does not let you format it wants you to
reformat your Flash drive. You will probably have to use a program like gparted and make
1 partition to Fat32. Your Flash has become unusable in other words.
 What does your properties say for flash drive? If you know how to use gparted that is a good way to format a USB device.

---

### Post by jakeeee on 2010-01-13
I did that.
It wont let me select my disc image.
Like i select it and put open and it doesnt show up in the window.
Gahh. This is hard to explain.

---

### Post by slooksterpsv on 2010-01-13
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

That's what i used, it works great and it's for Linux!

---

### Post by garvinrick4 on 2010-01-13
Are you trying to use a 12 gig Windows 7 .iso  ?

---

### Post by jakeeee on 2010-01-13
Uh no.
Its 3gb. haha.
But i got it to work. thanks :P

---

### Post by slooksterpsv on 2010-01-14
Let us know how you got it working so if someone searches for this thread, they know can see if it works for them (your steps).

---

### Post by Cheesemill on 2010-01-14
[http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/](http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/)

---

### Post by John Bean on 2010-01-14
> **slooksterpsv said:**
> [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

That's what i used, it works great and it's for Linux!

Yes and no. It's good when it works... which is not always the case. A clue lies in this quote from the requirements:> Microsoft Windows 2000/XP/Vista/7, or Linux. If you are having trouble with the Linux version, try the Windows version, it usually works better.Now there's an honest admission from the developer ;-)

---

