---
title: "Kodak camera not handled by Ubuntu-Christmas help needed"
date: 2009-12-20
forum: General Help
---

### Post by Mlava on 2009-12-20
HELP!!

I've tried loading photos from my Kodak EasyShare C340 for months.
It doesn't work!!  ](*,)
I am going home for Christmas and would like to show my family some photos
but can't unload them from the camera onto Ubuntu.

Please help, I am also complete beginner.
I see many people have this problem.  Apparently it's still unsolved.
Please step me through how to solve it.  
Thank you!!

---

### Post by Mark Phelps on 2009-12-21
The Kodak Easyshare software was written only for MS Windows, and as a result, will not work at all in Linux environments.

If you plugin your camera through a USB port, you should see a folder open on the desktop allowing you to browse through the pictures.

If you get no such folder, that means the generic USB driver can't recognize your camera -- and you will have to use MS Windows.

---

### Post by JuicyDOOM on 2009-12-25
Hello, I actually have the same problem but, different... well, I plug the camera, turn it on, then I get an error message that goes like this:

CANNOT MOUNT KODAK EASYSHARE C190
error installing camera
-60: Cannot lock device

I translated it form french but I think the ''-60: can't lock'' or something might be important, help would be greatly apreciated and thanks a lot ^^ Merry Chrtistmas By the way =D

---

### Post by coffeecat on 2009-12-25
According to a quick google, the C190 uses an SD card. Is that correct? If so, use an USB SD card reader. They don't have to be expensive. In fact, I got one similar to this:

[http://www.amazon.co.uk/Integral-Single-Slot-SDHC-Reader/dp/B000VY80AM/ref=sr_1_1?ie=UTF8&s=electronics&qid=1261761846&sr=8-1](http://www.amazon.co.uk/Integral-Single-Slot-SDHC-Reader/dp/B000VY80AM/ref=sr_1_1?ie=UTF8&s=electronics&qid=1261761846&sr=8-1)

... free with an SD card once.

---

### Post by Cotopaxi on 2010-01-08
Mlava,

Your Kodak C340 is supported by gphoto. See the following link:

[http://www.gphoto.org/proj/libgphoto2/support.php](http://www.gphoto.org/proj/libgphoto2/support.php)

so you can download &#8220;gphoto2&#8221;, which is in the repositories.

After that, you can download &#8220;gtkam&#8221; (for ubuntu) or &#8220;digikam&#8221; (for kubuntu).

They are also in the repositories.

"gphoto2" is only a command line tool, "gtkam" or "digikam" are applications with a graphical user interface, which are based on "gphoto2"

This should work!

---

