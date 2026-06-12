---
title: "Bluetooth File Sharing on 9.10"
date: 2009-10-31
forum: General Help
---

### Post by attercop on 2009-10-31
Does anyone know what the name of the thing i need to install is to get **Bluetooth File Sharing** to appear? I want to send files from my mobile to Ubuntu, and if it's in the repositories then it's well hidden!

---

### Post by attercop on 2009-10-31
Well i've tried everything but nothing has worked so far. It seems gnome-obex-server that used to make Bluetooth File Sharing appear in the Accessories menu in the older versions doesn't exist anymore. It seems that gnome-bluetooth is used now and gnome-obex-server isn't included. I've installed just about every bluetooth related package in the repos and Bluetooth File Sharing hasn't appeared yet. :(

---

### Post by Irihapeti on 2009-10-31
Install Blueman from the repositories. You end up with two bluetooth applets in the system tray, but that doesn't seem to matter - Blueman is the one with the blue background.

---

### Post by attercop on 2009-10-31
Ahh excellent. Thank you very much. That works. And to stop from having two icons i just unchecked the show icon option for the default bluetooth app.

---

### Post by Irihapeti on 2009-10-31
You're welcome. Glad to know there's a successful ending.

---

### Post by walmis on 2009-11-01
You should install version 1.21 from official ppa, the one in ubuntu archives is outdated, and quite buggy.
[https://edge.launchpad.net/~blueman/+archive/ppa]("https://edge.launchpad.net/%7Eblueman/+archive/ppa")

---

### Post by Irihapeti on 2009-11-01
> **walmis said:**
> You should install version 1.21 from official ppa, the one in ubuntu archives is outdated, and quite buggy.
[https://edge.launchpad.net/~blueman/+archive/ppa]("https://edge.launchpad.net/%7Eblueman/+archive/ppa")

Thank you. I'll do that.

---

