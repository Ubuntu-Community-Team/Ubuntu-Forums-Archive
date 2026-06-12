---
title: "Skype video dark (11.04)"
date: 2011-06-07
forum: General Help
---

### Post by Emanuele_Z on 2011-06-07
Hi guys,

Apparently Skype video is broken (i.e. is dark whilst is ok with Cheese as example) in Natty (11.04).
From this post ([http://forum.skype.com/index.php?showtopic=814145](http://forum.skype.com/index.php?showtopic=814145)) it looks like I'm not the only one having these issues.
Does anyone know why? Is it possible to fix it?

Cheers,

---

### Post by Emanuele_Z on 2011-06-09
No idea?

Cheers,

---

### Post by linuxinstalledfromhdd on 2011-06-09
Did you try any of these:

[http://ubuntuforums.org/showthread.php?t=1731392](http://ubuntuforums.org/showthread.php?t=1731392)

---

### Post by Emanuele_Z on 2011-06-11
> **linuxinstalledfromhdd said:**
> Did you try any of these:

[http://ubuntuforums.org/showthread.php?t=1731392](http://ubuntuforums.org/showthread.php?t=1731392)

I don't need to preload a library to make the webcam appear, the issue is that the colors are dark and get dark and darker during the conversation.

This didn't happen with the version of Skype in Ubuntu 10.10.
The webcam is physically ok, because with Cheese it works as expected.

Cheers,

---

### Post by Marcelo Ruiz on 2011-08-16
I run Maverick and had the same problem.
Try installing guvcview and start it. Open skype and under options test the video. On guvcview correct Gamma to around 200 and see if that improves the image.
The downside is that on other programs the webcam output will be too bright, but you can readjust the webcam running guvcview again.
Hope this helps!

---

