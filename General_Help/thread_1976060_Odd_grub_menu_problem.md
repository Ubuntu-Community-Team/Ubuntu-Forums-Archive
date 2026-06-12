---
title: "Odd grub menu problem?"
date: 2012-05-08
forum: General Help
---

### Post by zeating on 2012-05-08
I can only get to the grub menu if I use a flash drive and go into the flash drive from BIOS, then instead of opening the ubuntu installer from the flash drive it just opens up normal grub showing me my Ubuntu and windows install. This is the only way i've found to access the grub menu. Without doing this it just boots straight into windows. Any ideas?

---

### Post by wilee-nilee on 2012-05-08
Sounds like a hassle, lets get a better look at what's going on.

Download bootscript in the link, and extract it to your desktop from a usb boot or cd or from the running Ubuntu and run the command. A results.txt will appear, post the whole text for the forum users to look at and advise you.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```

---

### Post by kc1di on 2012-05-08
Sounds like you installed grub in your linux root partition instead of the the Master Boot Record.

You will need to reinstall grub- here how to do that. and make sure it's install in the MBR. 

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by zeating on 2012-05-08
> **kc1di said:**
> Sounds like you installed grub in your linux root partition instead of the the Master Boot Record.

You will need to reinstall grub- here how to do that. and make sure it's install in the MBR. 

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

If I reinstall grub with windows installed first will it show up on the menu?

---

### Post by kc1di on 2012-05-08
> **zeating said:**
> If I reinstall grub with windows installed first will it show up on the menu?

it should grub 2 is very good at finding windows.

---

