---
title: "Hide grub menu on multi-boot systems?"
date: 2012-03-08
forum: General Help
---

### Post by x-shaney-x on 2012-03-08
Is it possible to force the grub menu to hide on startup and auto boot the default OS unless a key is pressed?

I'm sure this used to be possible but I haven't done any messing around with grub much recently.

---

### Post by Jon Monreal on 2012-03-09
Is [this]("http://ubuntuforums.org/showpost.php?p=8682184&postcount=7") a solution to your problem?

---

### Post by x-shaney-x on 2012-03-09
Partially :)
It does hide the menu but holding shift as described in that post does not make the menu show :(

---

### Post by Jon Monreal on 2012-03-09
How about if you assign a value greater than zero, such as GRUB_TIMEOUT="1"?

---

### Post by x-shaney-x on 2012-03-09
Yes I actually tried "1" first and have since tried 0, 2 and 3 to no avail.

---

### Post by Jon Monreal on 2012-03-09
You can try [this]("http://ubuntuforums.org/showpost.php?p=9675923&postcount=10") to make sure it's checking for the keypress.

---

### Post by x-shaney-x on 2012-03-09
I have os-prober enabled so it already does the check.
When I hold the shift button, I do get a very brief white on black screen which says grub on it but no menu entries and it goes straight to booting up.

I can only assume something has changed since that solution was first posted.

---

### Post by Jon Monreal on 2012-03-09
> **x-shaney-x said:**
> I can only assume something has changed since that solution was first posted.

Actually, that's very close to the setup I'm using with grub2 version 1.99-12ubuntu5. Can you try "GRUB_HIDDEN_TIMEOUT=0"?

---

### Post by x-shaney-x on 2012-03-09
Ahh, that was actually the values I was changing.

I have now tried changing the values of GRUB_TIMEOUT as you first suggested.
Anything other than 0 shows the menu instead of hiding it.

Tried several combinations of both timeout entries now and just not getting it.

I originally had the files in /etc/grub.d chmod -x so grub was ONLY displaying my custom menu file (05_custom).
I have now chmod +x them and set everything back to default but still not working for some reason.

---

### Post by Jon Monreal on 2012-03-09
Here are the full (non-commented) contents of my /etc/default/grub:

```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

---

### Post by critin on 2012-03-09
Grub Customizer will let you unclick whatever you don't want to show and set default.

[http://www.ubuntugeek.com/grub-customizer-graphical-interface-to-configure-the-grub2burg-settings.html](http://www.ubuntugeek.com/grub-customizer-graphical-interface-to-configure-the-grub2burg-settings.html)

---

### Post by x-shaney-x on 2012-03-09
Ok I tried copying your entries EXACTLY and after updating grub and rebooting, I just get the grub menu displaying as normal.
Curious...

---

### Post by Jon Monreal on 2012-03-09
Could it be that you're using an even older version of grub? Or perhaps everything wasn't really set back to default (instead of your custom menu file)?

---

### Post by x-shaney-x on 2012-03-09
I am using grub in a fully updated 11.10 installed to MBR, which then chainloads other OS's or manual entries in 40_custom for things like Android.

It could be something has altered somewhere that makes it not "proper" default.

I am going to try disabling the 40_custom file later on and see if that makes a difference.

The fact it is working for would suggest it is a problem unique to me and my setup and I will assume that you have pointed me in the right direction so many thanks for that.

---

