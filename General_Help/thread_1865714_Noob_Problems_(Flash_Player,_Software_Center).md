---
title: "Noob Problems (Flash Player, Software Center)"
date: 2011-10-20
forum: General Help
---

### Post by XAuTomaT1CX on 2011-10-20
this is 11.10 btw

Before u read, Should I Just download ubuntu 10.04 instead, I don't believe I would have these problems?


Can't Delete World of Goo, it's in my games folder and doesn't give me a delete option so it's taking up space?

How do I Get Flash Player Working, what do I Install or Do ?

Keep Reading about command line & Terminals & Run, do i need to use any of this stuff to do what I want to do?

Lubuntu Software Center is not anywhere, so i can't download any Programs

---

### Post by 2F4U on 2011-10-20
Lubuntu, as far as I know, doesn't include the Software Center from the main Ubuntu distribution. However, there is a software manager available and I think it is called Synaptics. You should be able to deinstall World of Goo with it as well as install additional software.

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

> Keep Reading about command line & Terminals & Run, do i need to use any of this stuff to do what I want to do?

At the moment, you probably can get away without knowing the terminal. If you want to achieve more advanced topics, it may be worth learning about it.

---

### Post by 2F4U on 2011-10-20
If you absolutely need the Software Center, here is how to get it

[https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#How_to_install_Lubuntu_Software_Center_.28LSC.29](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#How_to_install_Lubuntu_Software_Center_.28LSC.29)

---

### Post by XAuTomaT1CX on 2011-10-20
Does Anyone know how I can get Flash Player working?

---

### Post by GrantStoner on 2011-10-20
sudo apt-get install adobe-flashplugin

---

### Post by dniMretsaM on 2011-10-20
> **XAuTomaT1CX said:**
> Does Anyone know how I can get Flash Player working?

If you use Firefox, you can use the add-on [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/) [[direct link](https://addons.mozilla.org/firefox/downloads/latest/161939/platform:2/addon-161939-latest.xpi?src=dp-btn-primary)]. It will install and configure the correct Flash version for your system. [Here's](http://ubuntuforums.org/showthread.php?t=1491268) a thread about it on the forums for more information/help. Otherwise you can install [FONT=Courier New]adobe-flashplugin[/FONT] from the repos, but I tend to shy away from that option for various reasons.

---

### Post by GrantStoner on 2011-10-20
> **dniMretsaM said:**
> If you use Firefox, you can use the add-on [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") [[direct link]("https://addons.mozilla.org/firefox/downloads/latest/161939/platform:2/addon-161939-latest.xpi?src=dp-btn-primary")]. It will install and configure the correct Flash version for your system. [Here's]("http://ubuntuforums.org/showthread.php?t=1491268") a thread about it on the forums for more information/help. Otherwise you can install [FONT=Courier New]adobe-flashplugin[/FONT] from the repos, but I tend to shy away from that option for various reasons.
Like dniMretsaM said, there's different flash plugins. If you don't like adobe you can ```
apt-get install flashplugin-nonfree
```as well. There's tons of options in the repos. Some work better than others. Some don't work at all. Or search synaptics for "flash" or "flashplugin" or the likes.

---

