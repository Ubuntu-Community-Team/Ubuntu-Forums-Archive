---
title: "Laptop stand by with ubuntu"
date: 2010-01-27
forum: General Help
---

### Post by Harshana85 on 2010-01-27
Hi,

I put stand by mood my laptop (HP Presario C301) by pressing Fn+f5 but then again once i want to use my lap i want to press the power button instead of touching the touch pad or a key like windows. can we change it?
Any way the most annoying problem is it doenst allow me to type the password again. A blank field box is there and it doesnt show the astrics when i type the password. I need to reboot the machine again to log. How to solve it?

Thank You.

---

### Post by efflandt on 2010-01-27
I wish I could offer (or find) a solution, same issue with a Compaq Presario V2000 laptop (32-bit Ubuntu 9.10 with standard modules except Broadcom B43).  Initially when it woke from suspend, I thought it came up with the login screen, but keyboard/mouse were unresponsive.

I did successfully hibernate and wake up from that (thaw) "once".  But now trying to wake from suspend just results in a black screen (no backlight) and no response, and trying to wake from hibernate shows the splash screen with "Waking up. Please wait...", but then results in same dark screen with no response.

I was also getting unresponsive keyboard entry (sometimes had to press some keys more than once during login, etc.) and erratic (delayed/jumpy) mousepad movement, but either "**un**checking" connect automatically for Auto eth0 (using B43 wireless instead), or system updates, seems to have resolved that.

In my case it appears to be related to ATI IXP AC'97 sound and modem, since before it hibernates. it mentions "atiixp: codec reset timeout" and "atiixp.modem: codec reset timout".  If I sudo rmmod snd+atiixp_modem, it eliminates the modem error, but still get atiixp: codec reset timeout.

VGA compatible ATI Radeon XPRESS 200M 5955 (PCIE) uses radeon, radeonfb
ATI IXP SB400 AC'97 Audio Controller (rev 02) uses snd-atiixp (snd_atiixp)
ATI SB400 AC'97 Modem Controller (rev 02) uses snd-atiixp-modem (snd_atiixp_modem)

---

