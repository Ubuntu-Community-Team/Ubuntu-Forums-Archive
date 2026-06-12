---
title: "SIP phone with alsa?"
date: 2006-03-15
forum: General Help
---

### Post by theOrange on 2006-03-15
Are there any linux SIP phones that use ALSA?

I have used X-Lite but it is OSS and therefore i can't have it ring to my speakers while i'm listening to VLC. I have to send all the sound to my USB headphones (dsp1). This also sucks b/c i can't hear the ring if i'm away from my seat. :(

Any other solutions for Breezy?

---

### Post by kaamos on 2006-03-15
[Ekiga](www.ekiga.org)!

How to install ->[http://ubuntuforums.org/showthread.php?t=144807](http://ubuntuforums.org/showthread.php?t=144807)

---

### Post by theOrange on 2006-03-15
[QUOTE=kaamos][Ekiga](www.ekiga.org)!

How to install ->[http://ubuntuforums.org/showthread.php?t=144807](http://ubuntuforums.org/showthread.php?t=144807)[/QUOTE]

Yeah, i tried Ekiga. I configured it with my work VIOP. It said the account registered but I could ony receive calls.  It SHOULD be a pretty simple config. I have a id, password, domain/registrar, and outboud proxy. But whenever i tried to make a call i got an "unknown host" error and abnormal termination of the call.

I looked on the site and googled but couldn't figure it out.  

Any ideas?

---

### Post by kaamos on 2006-03-15
As ekigas configuration for proxies seeems to be.. err.. non-existant, I suggest you post to the dev or users mailing list ([http://ekiga.org/index.php?rub=8](http://ekiga.org/index.php?rub=8) ) and see what the developers have to say about the problem.

You can btw use "ekiga-snapshot -d 4" in a terminal to get more info about the problem.

---

