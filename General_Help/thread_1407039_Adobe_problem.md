---
title: "Adobe problem"
date: 2010-02-14
forum: General Help
---

### Post by Drelynx on 2010-02-14
Hello id like to start by saying im a linux noob, ive used it before but i dont have alot of experience using it.

when i goto youtube it tells me i need adobe flash, when i goto install it the install crashes, can  anyone help me install this or get youtube working, im pretty sure im not doing it right. 

i just installed ubuntu 9.10 and ran update manager to get up to date stuff but that is all ive done since installing it.

---

### Post by scouser73 on 2010-02-14
[COLOR="Red"]**Installing Flash Player via the Adobe website**[/COLOR]

**1** - Go to [[COLOR="Red"]**Adobe Flash**[/COLOR]]("http://get.adobe.com/flashplayer/?promoid=BUIGP")

**2** - Select **.deb for Ubuntu 8.04+** from the drop down menu

**3** - Click **Agree & Install Now**

**4** - Select **Open With** **GDebi Package Installer** in firefox or save the file and install the **.deb** file that way

---

### Post by Drelynx on 2010-02-14
when i click install package i get this message.

Only one software management tool is allowed to run at the same time.

i tried rebooting and did it again and the same message pops up.

---

### Post by lovinglinux on 2010-02-14
> **Drelynx said:**
> when i click install package i get this message.

Only one software management tool is allowed to run at the same time.

i tried rebooting and did it again and the same message pops up.

Close Synaptic Package Manager, Software Center and Add/Remove manager if they are opened.

For 32bit see [this](http://lovinglinux.megabyet.net/?page_id=220#Removing-Conflicting-Plugins-2).

For 64bit see [this](http://ubuntuforums.org/showthread.php?t=1358591).

---

### Post by sendblink23 on 2010-02-14
Why does everyone suggest the hard way of installing Flash on linux, go SIMPLER

*Remove anything you have installed related to flash previously, from Synaptics or etc*

Simple Steps:

Applications > Ubuntu Software Center > Search: Flash

Install: Adobe Flash Plugin

Afterwards go to [http://youtube.com](http://youtube.com) to test it

That is it nothing else is there to it, it works perfectly on x86 & x64
I have over 7 computers(old ones pentium 4, new ones with i7 & phenom ii 965) I used the same simple thing from a Fresh Install and it has always worked since 8.04 till present 9.10.

*Note* ignore Flash 10, that appears in the Search, you don't really need it.

---

### Post by lovinglinux on 2010-02-14
> **sendblink23 said:**
> Why does everyone suggest the hard way of installing Flash on linux, go SIMPLER

*Remove anything you have installed related to flash previously, from Synaptics or etc*

Simple Steps:

Applications > Ubuntu Software Center > Search: Flash

Install: Adobe Flash Plugin

Afterwards go to [http://youtube.com](http://youtube.com) to test it

That is it nothing else is there to it, it works perfectly on x86 & x64
I have over 7 computers(old ones pentium 4, new ones with i7 & phenom ii 965) I used the same simple thing from a Fresh Install and it has always worked since 8.04 till present 9.10.

*Note* ignore Flash 10, that appears in the Search, you don't really need it.


Because if you have swfdec or gnash installed (as far as I remember one of them comes installed), then the Adobe plugin won't work. So, my link shows how to uninstall all plugins first, then install only the one from Adobe.

The other link I usually post is because there are several users experiencing problems under 64bit with flash from the repositories, which is not 64bit. Flash works, but sometimes [you can't interact with it](http://swiss.ubuntuforums.org/showthread.php?p=8555716). The solution is to install the 64 bit version.

---

