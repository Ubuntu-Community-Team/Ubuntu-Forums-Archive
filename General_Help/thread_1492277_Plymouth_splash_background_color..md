---
title: "Plymouth splash background color."
date: 2010-05-24
forum: General Help
---

### Post by stormcel on 2010-05-24
OK. I've been having a lot of fun customizing the plymouth splash.
I know how to change themes and I know how to set my graphic.
 
I've read all of the posts regarding plymouth and I have some simple questions.
 
-what is the RGB value of the current purply background?
-can I change the background color?
-how does one go about making a plymouth module? (.so file)
 
In my customizations I have been able to swap the logo but not the background, I would like to change the background color to black, barring that I would like to change the background of my image to match the current purple/lavender/magenta whatever color is there now.
And I have a sneaking suspicion that the bg color is set in the .so file
 
Thanks all!

---

### Post by chaumurky on 2010-06-04
Yeah, I'd like to know this too. I'm not a big fan of the Ubuntu Aubergine...

---

### Post by wojox on 2010-06-04
Try running this in the terminal:

```
gksudo -u gdm dbus-launch gnome-appearance-properties 
```

---

### Post by whitepine on 2010-06-04
To change splash background color in plymouth, open as root:   '/lib/plymouth/themes/ubuntu-logo/ubuntu-logo.script'

Go to lines 166 and 167.  Change the colors to whatever you want.  The colors refer to RGB colors divided by 255.  So 0.16, 0.00, 0.12 is RGB 41, 0.00, 31 Aubergine! 

Then:

sudo update-initramfs -u

---

### Post by b3125312k on 2010-07-12
> **whitepine said:**
> To change splash background color in plymouth, open as root:   '/lib/plymouth/themes/ubuntu-logo/ubuntu-logo.script'

Go to lines 166 and 167.  Change the colors to whatever you want.  The colors refer to RGB colors divided by 255.  So 0.16, 0.00, 0.12 is RGB 41, 0.00, 31 Aubergine! 

Then:

sudo update-initramfs -u

Thank you very much. Excellent!

---

### Post by roshgorg on 2012-05-29
Is it possible to update the plymouth theme image and logo to something else in the live cd ?

---

### Post by uRock on 2012-05-29
Two year old thread. Please start a new one on this topic.

Thread Closed

---

