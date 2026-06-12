---
title: "Problem With Flash"
date: 2010-03-16
forum: General Help
---

### Post by 131bobby313 on 2010-03-16
Ok, I went to the adobe website and installed flash .deb for ubuntu, and it installed correctly.

But I went to watch a youtube video and its saying I need to install the newest adobe flash player, or Javascript is turned off. I have installed the latest version of flash that adobe offers, and I went to mozilla firefox settings and it says that javascript is turned on.

Anybody know what the problem is? Am I suppose to install flash another way? Please somebody help.

---

### Post by xtremesupremacy3 on 2010-03-16
Ok, I'm going to assume that your using Ubuntu 9.04+, if not please let me know.

Click on Applications> Ubuntu Software Centre

And search for Adobe Flash plugin, install that and try again

---

### Post by 131bobby313 on 2010-03-16
8.04 Sorry

---

### Post by xtremesupremacy3 on 2010-03-16
Do you get a bar up at all about missing plugins?

---

### Post by 131bobby313 on 2010-03-16
Nope, Just this.
"Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. [Get the latest Flash player]("http://www.adobe.com/go/getflashplayer/")."

---

### Post by xtremesupremacy3 on 2010-03-16
Okay, try this, maybe it works:

Open a terminal (Applications > Accessories > Terminal)

and copy and paste this there:

```
sudo apt-get install flashplugin-nonfree
```

I hope this helps,

Ps. Don't forget to restart Firefox

---

### Post by 131bobby313 on 2010-03-16
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting adobe-flashplugin instead of flashplugin-nonfree
adobe-flashplugin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 373 not upgraded.


Hmm, I Don't think it has anything to do with the installation.. I just don't understand what else it could be

---

### Post by 131bobby313 on 2010-03-16
anybody else have any ideas?

---

### Post by soltanis on 2010-03-16
Besides a newer Ubuntu?

Search your system for libflashplayer.so and copy it into the directory ~/.mozilla/plugins/ (create it if necessary).

```

sudo updatedb
locate libflashplayer

```
Will help you find the file.

---

### Post by sandyd on 2010-03-16
can you do ```

ls /usr/lib/mozilla/plugins
```

---

### Post by lyall on 2010-03-16
look at this link for **RestrictedFormatsFlash**
[https://help.ubuntu.com/community/RestrictedFormats/Flash?action=show&redirect=Flash]("https://help.ubuntu.com/community/RestrictedFormats/Flash?action=show&redirect=Flash")

read the instruction and install for your version of Ubuntu

good luck and have fun learning

---

### Post by wojox on 2010-03-16
> **131bobby313 said:**
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting adobe-flashplugin instead of flashplugin-nonfree
adobe-flashplugin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 373 not upgraded.


Hmm, I Don't think it has anything to do with the installation.. I just don't understand what else it could be

Why do you have 373 upgrades?

---

### Post by lovinglinux on 2010-03-16
See [this](http://lovinglinux.megabyet.net/?page_id=220#Removing-Conflicting-Plugins-2).

---

