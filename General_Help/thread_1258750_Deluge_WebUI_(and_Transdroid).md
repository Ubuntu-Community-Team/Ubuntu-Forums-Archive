---
title: "Deluge WebUI (and Transdroid)"
date: 2009-09-05
forum: General Help
---

### Post by jzraikes on 2009-09-05
I'm using Deluge 1.1.9 and I can't work out how to get the WebUI up and running. I've googled it, but only found out-of-date information that doesn't help me. Can anyone help?
The reason I want to get the WebUI to work is so I can use Transdroid on my Android phone to control my torrents, so if anyone has an Android phone and already has it all set up with Transdroid and Deluge then any help with that would also be appreciated. 
(I know Transdroid isn't directly linked to Ubuntu, so this probably isn't the best place to ask for help with using it, but I can probably work it out myself anyway, I just need help with Deluge)

Thanks in advance.

---

### Post by lovinglinux on 2009-09-05
[http://ubuntuforums.org/showthread.php?t=1114965](http://ubuntuforums.org/showthread.php?t=1114965)

---

### Post by jzraikes on 2009-09-06
> **lovinglinux said:**
> [http://ubuntuforums.org/showthread.php?t=1114965](http://ubuntuforums.org/showthread.php?t=1114965)
Thanks. I set it up as per the instructions, but how can I tell if the daemon is running or not? 
The notification icon is for the GTK client and when the client is closed the icon disappears (I presume, leaving the daemon running)
Thanks in advance.

**Edit:** Sorry, worked it out reading the Deluge FAQ. Different question though: Will the WebUI automatically update itself or do I have to download and install newer versions as they are released? I ask because the 'ajax' version is labelled 'alpha'
Thanks again

---

### Post by lovinglinux on 2009-09-06
> **jzraikes said:**
> Thanks. I set it up as per the instructions, but how can I tell if the daemon is running or not? 
The notification icon is for the GTK client and when the client is closed the icon disappears (I presume, leaving the daemon running)
Thanks in advance.

**Edit:** Sorry, worked it out reading the Deluge FAQ. Different question though: Will the WebUI automatically update itself or do I have to download and install newer versions as they are released? I ask because the 'ajax' version is labelled 'alpha'
Thanks again

It will update when a new version of the webui is available. The package deluge-webui depends on deluge-common, which is required for deluge too.

---

### Post by jzraikes on 2009-09-06
> **lovinglinux said:**
> It will update when a new version of the webui is available. The package deluge-webui depends on deluge-common, which is required for deluge too.
Ah of course, thanks for the help :)

---

