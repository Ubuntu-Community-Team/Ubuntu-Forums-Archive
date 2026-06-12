---
title: "Password help"
date: 2010-05-21
forum: General Help
---

### Post by amo512 on 2010-05-21
Hi,
I have just bought a used Dell Inspiron 910 with Ubuntu installed. I can get into the system fine as there is no user password. 
However if I want to add a new user or change the wireless settings, it keeps asking for a password of the previous owner, and I don't have this.
 
Can anyone help me please?
Thanks
Am

---

### Post by mikewhatever on 2010-05-21
Rather then using someone else's account or even a new one, it would be best to perform a clean installation.
You can also reset the current user password from recovery mode.
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Peter09 on 2010-05-21
If the password is blank try just hitting return when it asks for a password.

---

### Post by amo512 on 2010-05-21
Hi, I don't have a CD Rom with the laptop so I can't do a new install. I've tried holding down the shift key and escape key but it just boots up the system.
Exactly when should I press the key.
Thanks

---

### Post by Peter09 on 2010-05-21
start holding the shift key as soon as you see the Bios boot text.

---

### Post by amo512 on 2010-05-21
It is now showing this prompt:
 
MBR 2FA:

---

### Post by Peter09 on 2010-05-21
Mmm - no idea, it may be that you interupted the bios boot. Try holding the shift key as soon as the Bios text disappears.

---

### Post by mikewhatever on 2010-05-21
> **amo512 said:**
> Hi, I don't have a CD Rom with the laptop so I can't do a new install. I've tried holding down the shift key and escape key but it just boots up the system.
Exactly when should I press the key.
Thanks

You don't need a cdrom, a usb stick would do.
Try hitting Esc instead of Shift right after the BIOS screen. The older versions of Ubuntu had Grub1, which used Esc to show its menu.

---

### Post by amo512 on 2010-05-21
Still just boots up

---

### Post by Peter09 on 2010-05-21
As Amo512 said you may need to use esc if you are not running LUCID. You will need to hit the escape key multiple times to ensure that you get to the grub menu.

---

### Post by amo512 on 2010-05-21
Hi, I am running 8.04.
I have tried the escape key too, it appears that the Grub menu just flashes for 1 second and then it says starting up...

---

### Post by bapoumba on 2010-05-21
If this is a laptop you bought from someone else, they should give you the password.
Other than that, usb install is easy:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by mikewhatever on 2010-05-21
Can you post the output of the following:

cat /boot/grub/menu.lst

If that is Dell's custom installation, I wouldn't be surprised if the recovery mode was disabled.

---

### Post by amo512 on 2010-05-21
Hi, I have tried to increase the Grub menu time as it is "O", but it will not allow me to save the file, as it keeps asking for the password

---

### Post by mikewhatever on 2010-05-21
Well, you need the password to edit system files. You are pretty much stuck there, and the reinstall option seems to be the next logical step. ;)

---

### Post by Peter09 on 2010-05-21
As soon as you see the Grub menu hit the down arrow key --- quick reflexes needed for Linux Geeks :-)

---

### Post by mikewhatever on 2010-05-21
> **Peter09 said:**
> As soon as you see the Grub menu hit the down arrow key --- quick reflexes needed for Linux Geeks :-)

Well, I really don't think anyone can go faster then 0 seconds. :P

---

### Post by amo512 on 2010-05-21
well I can't do it!
 
Can't the grub menu time be changed via the terminal?

---

### Post by Peter09 on 2010-05-21
:)
 
He did say
 
> 
Hi, I am running 8.04.
I have tried the escape key too, it appears that the Grub menu just flashes for 1 second and then it says starting up...

 
So there is a chance that he could get there ...... The people who require support just haven't got the reactions these days :)

---

### Post by mikewhatever on 2010-05-21
> **amo512 said:**
> well I can't do it!
 
Can't the grub menu time be changed via the terminal?

Sure it can, provided you have the password.

---

### Post by amo512 on 2010-05-21
Hi, I have tried to install v10.4 via USB however the laptop just hangs at startup and will not load the USB files even though I have selected it as the startup in the BIOS.
Its a Dell 910.
 
Thanks

---

