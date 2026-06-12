---
title: "Anybody know if there is a system tray indicator for devices?"
date: 2010-11-14
forum: General Help
---

### Post by inameiname on 2010-11-14
I swear I've heard of one of these a while back, but I just can't place where and what it was. Does anybody know of an apt indicator or the like that is a simple device icon on the system tray or something like that in Windows where you can click and perhaps unmount, safely remove, and maybe eject devices?

---

### Post by inameiname on 2010-11-15
I found one that might do the job, but I'm unsure of whether or not it just 'ejects', or 'safely removes' devices. 

sudo apt-get install ejecter

Here is the apt-cache show results for it:

```

Description: application to unmount easily and safely external devices
 Ejecter is a simple menu that sits in the system notification area, providing
 you a quick way to unmount an external peripheral such as USB pendrive, CD/DVD
 disk, external hard disk and so. 
 
 Ejecter will sleep behind the scenes and show an icon in the system tray when
 one or more devices are connected to your computer.

```

Ideally, one that can 'unmount', 'eject', and 'safely remove', would be grande, but I'll be happy for one that can just 'safely remove', as that is what I most need when it comes to external hard drives and flash drives and the like.

---

### Post by stinkeye on 2010-11-15
[**_[COLOR="DarkRed"]indicator-usb[/COLOR]_**]("http://dl.dropbox.com/u/7138409/indicator-usb/indicator.html")

---

### Post by inameiname on 2010-11-15
Thanks for the link. It seems very similar to both 'ejecter' that I found and the 'disk unmounter' that is already available as a potential indicator. I guess it all comes down to which looks better, as they all seem to do the same, professing a safe removal. Hunkydory.

---

### Post by inameiname on 2010-11-15
I think by going on looks, 'ejecter' beats the others. Guess I'll mark this as solved, though an ultimate one that could be a quick and easy unmounter/ejecter/safely-remover would be super duper.

---

