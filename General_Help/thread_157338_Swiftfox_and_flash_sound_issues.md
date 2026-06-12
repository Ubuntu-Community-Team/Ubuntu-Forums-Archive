---
title: "Swiftfox and flash sound issues"
date: 2006-04-08
forum: General Help
---

### Post by Third Thoughts on 2006-04-08
I recently tried out swiftfox, and I'm really impressed, but I've got just one problem. Under firefox I had to edit the /etc/mozilla-firefox/mozilla-firefoxrc file in order to make firefox use the aoss sound wrapper (I added the line FIREFOX DSP="aoss". This is the only line in the file.) Before I did this sound in flash was really low quality. I can't find the equivalent swiftfox file to edit. I found the folder it would be in (/swiftfox/defaults/) and made a sym link to the mozilla-firefoxrc file, but that didn't work. I tried changing the name to mozilla-swiftfoxrc, and just swiftfoxrc, but those didn't work any better. What did work was running swiftfox through aoss (aoss /swiftfox/firefox), but when I do that swiftfox loads without all of my extensions or profile information. Anyone know how I can fix this issue? Thanks

~Andrew S.

---

### Post by Third Thoughts on 2006-04-08
Well I managed to get it so the command aoss /swiftfox/firefox, loaded up with the extenstions and stuff. So I've got a working system, but if anyone knows I'd like to know where the swiftfox configuration file is anyways. Thanks again.

~Andrew S.

---

### Post by ynui on 2006-08-01
Any chance you maybe able to elaborate to how you manage to solve this issue? if that was the case? Would be very much appreciated. Thanks

---

### Post by wh0rd on 2006-08-25
I have the same issue. Swiftfox is really fast and super, but kinda handicapped without the flash sound.

---

### Post by wh0rd on 2006-09-22
Load swiftfox with aoss. So just change the shortcut/launcher properties to:

> aoss swiftfox

---

