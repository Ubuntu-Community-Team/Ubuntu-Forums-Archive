---
title: "tx2 1025 dx screen issues"
date: 2011-01-29
forum: General Help
---

### Post by loganbell45 on 2011-01-29
Hi all, I'm having trouble getting my touch screen working correctly with ubuntu 10.10, the touch input doesn't work at all, and when I use the pen for a very short time, the system seems to crash, and I'm unable to do anything but restart the computer, can anyone point me in the direction of a solution? Sorry if you always get this kind of question ):P

---

### Post by Favux on 2011-01-29
Hi loganbell45,

Welcome to Ubuntu forums!

The symptoms you are describing are consistent with old firmware.  Right now your firmware probably only supports single finger touch.  Ubuntu accidently left out single finger touch in the default Maverick hid-ntrig.ko.  The hid-ntrig.ko is the kernel driver/module that establishes usb communication with your N-trig digitizer.

So if you have a Windows partition you want to use Windows to update your firmware.  See near the top of the [N-trig HOW TO]("http://ubuntuforums.org/showpost.php?p=7863677&postcount=1").

If you no longer have access to Windows you'll need to patch the hid-ntrig.ko with Ayuthia's patch to restore single finger touch.  See 1) Maverick b) in the N-trig HOW TO.

Hope this is helpful.

---

### Post by loganbell45 on 2011-01-30
Thank you for the response, it seems to have fixed any issues

---

### Post by Favux on 2011-01-30
Good!  Could you mark the thread solved?  In thread tools above your first post.

---

