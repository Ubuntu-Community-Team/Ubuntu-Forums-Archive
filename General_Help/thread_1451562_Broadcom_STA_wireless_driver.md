---
title: "Broadcom STA wireless driver?"
date: 2010-04-10
forum: General Help
---

### Post by ivandobski on 2010-04-10
Having recently updated my XP netbook to UNR and being more than happy with the results I decided to bin Vista on my "proper" laptop and installed Ubuntu 9.10. Prior to doing so I ran it off the USB and all was well, the Broadcom STA wireless driver was detected and could be activated ok. So, did the full install and now it won't play.

Basically when selecting the driver, clicking activate and then sticking my password in it doesn't actually do anything - just reverts back to the "This driver is not activated" screen.

Any help would be much appreciated, cheers.

---

### Post by wojox on 2010-04-10
Do you have an Ethernet cable plugged in while Activating it?

---

### Post by 2hot6ft2 on 2010-04-10
Since you don't say which broadcom it is here you go:
[The Definitive 9.10 Broadcom Solution Guide]("http://ubuntuforums.org/showthread.php?t=1368699")

---

### Post by ivandobski on 2010-04-10
No, wireless only.

I assumed I'd need a wired connection but it has worked wirelessly running direct so now I'm stuck really.

---

### Post by 2hot6ft2 on 2010-04-10
> **ivandobski said:**
> No, wireless only.

I assumed I'd need a wired connection but it has worked wirelessly running direct so now I'm stuck really.
System > Administration > Software Sources
Check the box for
Installable from CDROM/DVD
Put the livecd in
And click Close
Then check
System > Administration > Hardware Drivers
again
Might need to
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo apt-get update
```
You will have to enter your password which wont be displayed just type it in and hit Enter
Wait for it to finish then check
System > Administration > Hardware Drivers
again.

Don't forget to go back to Software Sources and uncheck the box once you have the driver installed and remove the livecd.

---

### Post by wojox on 2010-04-10
Yes you need to have access to the driver to Activate it. 2hot6ft2's suggestion should work for you.

---

### Post by ivandobski on 2010-04-10
Thanks but it's still not having it... I've got a couple of distros turning up soon so I'll hold off till then and see what happens.

---

### Post by wojox on 2010-04-10
Did you get the wireless driver activated with 2hot6ft2 suggestion?

---

### Post by ivandobski on 2010-04-10
No I didn't. It just doesn't seem to recognise the drivers. I've put the UNR back on and it's the same as before - works ok from the USB but doesn't recognise the drivers when actually installed.

---

