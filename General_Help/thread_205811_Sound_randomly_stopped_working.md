---
title: "Sound randomly stopped working"
date: 2006-06-29
forum: General Help
---

### Post by BlacKsheep88 on 2006-06-29
My sound randomly cut out and will not work now...it was working literally 10 minutes ago and now I can't hear anything, not even the start up sound. I made no changes and did not even open the terminal during this time. Help?

---

### Post by woedend on 2006-06-29
but, did you reboot(i figured you had because you mentioned the startup sound).
Double click the little sound icon by the time.
Go to file, then to change device.  
Number 0 Should be the right sound card, is it?
Debian has a bad way of letting usb devices (mics/cameras/etc) grab default sound card on boot.

---

### Post by BlacKsheep88 on 2006-06-29
I just got this notification from Amarok:
"audio device is unavailable; busy

xine parameter"

Do I have to reinstall xine?

---

### Post by woedend on 2006-06-29
you can, but 99% chance it won't help a thing.  Did you try what I had asked?

---

### Post by hvbakel on 2006-06-30
I think the problem that you're having is that one program is using your soundcard and blocking it for use with other programs. Do you have any other sound player or sound server (such as the arts daemon on kde or perhaps esd) running at the same time?

---

