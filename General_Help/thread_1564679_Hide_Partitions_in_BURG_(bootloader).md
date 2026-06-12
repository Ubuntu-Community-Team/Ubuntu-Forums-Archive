---
title: "Hide Partitions in BURG (bootloader)"
date: 2010-08-30
forum: General Help
---

### Post by [::AP::] on 2010-08-30
Greetings - 

I have recently installed the BURG bootloader successfully.:D

However, I wish to hide some partitions from showing up.

I have already used the fold command ('f'), and that worked beautifully, but there are still two more I wish to hide. 

They are the Dell Utility and Windows XP Embedded,  which I believe is the Dell Media Direct partition. 

I wish to hide...

'/dev/sda1'
'/dev/sda5'

How would I achieve this in BURG? What entries must I make to '/etc/default/burg'? :confused:

I have BURG-manager (kind of like StartUp-manager or BootUp-manager), if that helps...

I uploaded a picture of my BURG to ImageShack. I wish to hide the 2nd and 4th listed partitions. 

[[IMG]http://img833.imageshack.us/img833/7006/25746123.png[/IMG]](http://img833.imageshack.us/i/25746123.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

[http://img833.imageshack.us/img833/7006/25746123.png](http://img833.imageshack.us/img833/7006/25746123.png)

Thank you,

[::AP::]

---

### Post by Autodidact on 2010-08-30
burg is NOT a bootloader, it just decorates the grub bootloader.

You need to edit the menu.lst file.
Open terminal and do something like this:
```
sudo gedit /boot/grub/menu.lst
```

Now remove/comment the menu entries you don't like to show up.

---

### Post by [::AP::] on 2010-08-30
> **Autodidact said:**
> burg is NOT a bootloader, it just decorates the grub bootloader.

#-o  Oops. I knew that. 

Sorry, I am a Linux newbie, please excuse that mistake. 

Anyways, thank you, I will do this...

[::AP::]

---

### Post by Autodidact on 2010-09-01
> **'[::AP::] said:**
> Sorry, I am a Linux newbie, please excuse that mistake.
I did not intend to be rude, just clear :)

Kind Regards,

---

### Post by [::AP::] on 2010-09-01
> **Autodidact said:**
> I did not intend to be rude, just clear :)

Kind Regards,

I know, thanks!

[::AP::]

---

