---
title: "Geek Wisdom"
date: 2010-06-15
forum: General Help
---

### Post by TheGreatNevada on 2010-06-15
Hi guys!

Ive been running Fedora now for a little while and i Love it. My question is I cannot watch anything at [http://tvampd.com](http://tvampd.com) without rebooting into my windows boot. I hate being so dependent on windows any ideas? For example I cannot watch the new big bang theory episode [http://tvampd.com/big-bang-theory/the-lunar-excitation](http://tvampd.com/big-bang-theory/the-lunar-excitation) .

Perhaps theres a special player im missing? I dont think they are using any strange codecs or anything

I use firefox btw

Thanks!!

---

### Post by jerome1232 on 2010-06-15
I was able to watch it on the second link, looks like it's just using my totem plugin, it's a plain xvid encoded video. Does the link below work?

[http://veehd.com/video/3815791_The-Big-Bang-Theory-S03E23-The-Lunar-Excitation](http://veehd.com/video/3815791_The-Big-Bang-Theory-S03E23-The-Lunar-Excitation)

---

### Post by TheGreatNevada on 2010-06-15
thanks for the super quick reply.

No that link you sent me didnt work :( Any ideas?

---

### Post by WorMzy on 2010-06-15
You need the flash plugin. Unfortunately, *which* flash plugin you need depends on your OS' architecture. Open a terminal and run ```
uname -m
``` Post the output here.


I'm curious why you're asking here, when Fedora have their own community-driven [help forums]("http://forums.fedoraforum.org/forumdisplay.php?f=3")..?

---

### Post by TheGreatNevada on 2010-06-15
Im always wondering around this forum cause i used to have ubuntu. Never really found a fedora forum i liked as much ..

uname outputs 
i686

---

### Post by Frogs Hair on 2010-06-15
The video is using DivX web player on my computer.

---

### Post by WorMzy on 2010-06-15
Go here: [http://get.adobe.com/flashplayer/]("http://get.adobe.com/flashplayer/") and download the YUM for Linux version. Then open a terminal and cd into the download directory, then run ```
su -c 'rpm -ivh adobe-release-i386-1.0-1.noarch.rpm'
``` then, if you want to keep it updated, run ```
su -c 'rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-adobe-linux'
```

EDIT: Forgot the installation line:
Run ```
su -c 'yum install flash-plugin'
```

---

### Post by jerome1232 on 2010-06-15
> **Frogs Hair said:**
> The video is using DivX web player on my computer.

This.

Your just assuming he needs flash, this particular video isn't using flash. It's using the totem plugin. (I can right click it and play it in totem)

I'm not sure what the equivalent on fedora would be, they differ between kde and gnome I think too. I'm sure an mplayer firefox plugin would play the video.

---

### Post by WorMzy on 2010-06-15
Not all the links on tvampd.com use DivX. Most link to flash content.

---

### Post by TheGreatNevada on 2010-06-15
Yah thats right . Most flash works fine. Just the VeehD and similar website do not.

---

### Post by WorMzy on 2010-06-15
If other flash sites work fine, then you must already have flash installed; in which case ignore my previous advice. 

I believe that vlc-plugin will play divx if you can't/don't want totem. [This link]("http://www.videolan.org/vlc/download-fedora.html") tells you how to install it.

---

### Post by jerome1232 on 2010-06-15
> **WorMzy said:**
> Not all the links on tvampd.com use DivX. Most link to flash content.

ah. I just went to one now I'm the one assuming :P

---

### Post by TheGreatNevada on 2010-06-15
the flash content works for me. any tips on getting the divx up and running?

---

### Post by WorMzy on 2010-06-15
> **jerome1232 said:**
> ah. I just went to one now I'm the one assuming :P

No worries, you had me pretty confused for a minute there. :p


@ TheGreatNevada: The vlc-plugin I linked you to in my previous post should do the trick, but I don't get video controls (to play/pause, change volume, etc) with it. The totem-plugin is probably the way to go.

```
su -c 'yum install totem-plugin'
```

EDIT: It might be called totem-mozplugin instead of totem-plugin.

---

### Post by TheGreatNevada on 2010-06-15
thanks! I'll try that as soon as i get home :popcorn:

---

