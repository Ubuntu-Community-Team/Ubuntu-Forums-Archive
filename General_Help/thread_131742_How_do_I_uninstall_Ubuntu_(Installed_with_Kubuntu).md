---
title: "How do I uninstall Ubuntu (Installed with Kubuntu)"
date: 2006-02-17
forum: General Help
---

### Post by Zach1188 on 2006-02-17
I am a big fan of KDE, and I wanted to try Gnome. So I used "sudo apt-get install ubuntu-desktop". I hate Gnome, it confuses me (I have been using Windows for about 9 years now, and KDE is a little similar). So now the login screen shows up as ubuntu. I tried typing "sudo apt-get remove ubuntu-desktop" and "sudo apt-get remove kubuntu desktop", and then tried reinstalling KDE. Everything works fine like it should, but it seems Gnome is still on the system. The login screen is still the Ubuntu one. How do I completely uninstall it (And ALL the applications that came with it (Except system files/files needed by KDE)) ?


P.S.
I wasn't sure which forum to post this in, so sorry if it is the wrong one.

---

### Post by kenweill on 2006-02-17
Install KDM and remove GDM.
Im just not sure how to activate 1 when the 2 are installed.

---

### Post by aysiu on 2006-02-17
Try [this](http://www.ubuntuforums.org/showthread.php?t=96046).

---

### Post by Zach1188 on 2006-02-18
Thanks, that did the trick.

---

### Post by nickle on 2006-02-18
I think it is really important to dump most of the Gnome stuff to really appreciate KDE/Kubuntu at its sleekest. I tried the tip by Aysiu and it partly worked. In fact it removed Kubuntu itself and just left me with the KDE interface minus some bits. For example konquerer was missing (????). I don't know why this was..
In any case I then reinstalled Kubuntu and I am really happy with the result.

Clearly KDE users are at a disadvantage since Ubuntu is synonimus with Gnome. So if you make the mistake like many new users who want to install KDE but install the ubuntu desktop (which is gnome) and find the result horrible, don't dispair that Kubuntu is crap; you simply need to remove all the gnome stuff that was (probably inadvertently) installed.

Please note I have nothing against Gnome. However, as I have said several time in the past, Ubuntu would be better if it made a better and clear distinction between Ubuntu the Linux distribution and the 2 desktop environments. As it stands Ubuntu, the brand, the distribution, and the gnome  desktop are synonimus and Kubuntu is some kind of after thought...

---

### Post by aysiu on 2006-02-18
[QUOTE=nickle]I think it is really important to dump most of the Gnome stuff to really appreciate KDE/Kubuntu at its sleekest. I tried the tip by Aysiu and it partly worked. In fact it removed Kubuntu itself and just left me with the KDE interface minus some bits. For example konquerer was missing (????). I don't know why this was..[/QUOTE] Did you use the HowTo when I *first* wrote it? Because I've revised it since then, and I'm pretty sure it works now.

---

### Post by nickle on 2006-02-18
[QUOTE=aysiu]Did you use the HowTo when I *first* wrote it? Because I've revised it since then, and I'm pretty sure it works now.[/QUOTE]

I cut and pasted your code yesterday....

---

### Post by aysiu on 2006-02-18
[QUOTE=nickle]I cut and pasted your code yesterday....[/QUOTE] Hm. That's odd. Because the way I got that code was from doing a *fresh* Kubuntu installation (nothing else) and then seeing what *additional* packages would be installed along with *ubuntu-desktop*.

Zach1188, if you're still around, did you have that same problem (the code removing Konqueror)?

---

### Post by nickle on 2006-02-18
It was kind of frightening to see all the packages disappearing...lol. But my system rebooted ok but back to the raw kde 3.5.1, i.e. all the gnome stuff was gone as expected, but all the kubuntu extras were gone as well. I was surprised about this, and especially that konquerer was gone too. I cannot explain this.

As I say I just cut an pasted your one very long line of code....

---

### Post by Single on 2006-02-19
Try install back the package kubuntu-desktop (with the kde 3.5.1 repository enabled) . This may give you back what you want.

---

### Post by nickle on 2006-02-19
Getting the missing stuff reinstalled was not an issue... Many thanks though for the comment...

---

