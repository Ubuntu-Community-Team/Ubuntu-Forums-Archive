---
title: "How to turn on numlock by default"
date: 2010-03-26
forum: General Help
---

### Post by joachim10022 on 2010-03-26
Hi

I would like to know, how to have numlock on by default during the log-in screen as my password is partly with numbers and it is annoying to turn on numlock manually.
Can one change this or do i have to live with always turning on numlock before?

Thanks

---

### Post by philinux on 2010-03-26
Install numlockx from synaptic or terminal

---

### Post by cogier on 2010-03-26
This is normally done in the BIOS. You need to check which key to hit when you boot, usually F2 or the Delete key and see if you can change the setting there.

**WARNING **You can make your computer unusable if you mess with some parts of the BIOS (Having said that take care and all should be OK)

---

### Post by joachim10022 on 2010-03-26
> **philinux said:**
> Install numlockx from synaptic or terminal

I did try that, but this only enables numlock after i logged in to my account

---

### Post by philinux on 2010-03-26
> **joachim10022 said:**
> I did try that, but this only enables numlock after i logged in to my account

[https://help.ubuntu.com/community/NumLock](https://help.ubuntu.com/community/NumLock)

---

### Post by stinkeye on 2010-03-26
Thanks philinux, that had been annoying me for a while.

---

### Post by joachim10022 on 2010-03-27
> **philinux said:**
> [https://help.ubuntu.com/community/NumLock](https://help.ubuntu.com/community/NumLock)

"Enabling NumLock during startup and before login
Here's how to enable numlock to stay on during startup and before you login so it is on before you enter your username password into the logon screen

Enabling NumLock in GDM (as used in Ubuntu Gnome and Xubuntu XFCE)
If you are using GDM you can use numlockx:

Install numlockx using apt-get, aptitude or Synaptic
**In Hardy and Gutsy**, edit /etc/gdm/Init/Default. For older versions of ubuntu edit /etc/X11/gdm/Init/Default instead.
Find the line
exit 0
Add the following code above that line
if [ -x /usr/bin/numlockx ]; then
  /usr/bin/numlockx on
fi
Also.. even if the numlock light on your keyboard is on.. there is a setting that can override it. System->Preferences->Keyboard.. then click the "Mouse Keys" tab and make sure to uncheck "Pointer can be controlled using the keypad"."

-- Will this also work for Karmic?

---

### Post by stinkeye on 2010-03-27
Worked for me on karmic.

---

### Post by Sonia10 on 2010-03-27
This the simple answer that you can go to BIOS and do the Number lock by default or you can do it by pressing the number lock key also...............................


The general discussion of number lock is excellent:p:D

---

### Post by stinkeye on 2010-03-27
> **Sonia10 said:**
> This the simple answer that you can go to BIOS and do the Number lock by default or you can do it by pressing the number lock key also...............................


The general discussion of number lock is excellent:p:D
What this fixed was that if I logged out and went to log back in the numlock was off, even if it was enabled in the bios and was on when I logged out.

---

