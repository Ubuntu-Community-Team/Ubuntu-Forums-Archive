---
title: "flashplugin-nonfree not working correctly"
date: 2009-10-30
forum: General Help
---

### Post by zdunham on 2009-10-30
Hi all. I have no idea where to start with this one. I just installed Xubuntu 9.10 and when I first went on the internet with Firefox anything that needed flash said I needed to get flash. So I went to Adobe's website and downloaded there .deb package adobe-flashplugin and it messed up all sorts of things. I was getting errors from synaptic anytime I tried to install anything. So I did this:

```

find / -name adobe-flashplugin

```

And I deleted anything that had to do with it. Then I made a backup copy of /var/lib/dpkg/status just in case I messed it up. I then went into that file and removed that part that had to do with adobe-flashplugin. After this I could now install things again but I still had no flash. Then I installed flashplugin-nonfree and flashplugin-nonfree-extrasound and everything went smooth. The only problem is when I visit any website that has a flash app it still comes up with the message about needing to get flash. 

I have no idea where to start with this one and any help would be awesome. Thanks in advance.

---

### Post by zdunham on 2009-10-30
OK, now it works sometimes but not every time. Interesting.

---

### Post by lovinglinux on 2009-10-30
See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004).

---

### Post by mac9416 on 2009-10-30
Someone in [another thread]("http://ubuntuforums.org/showthread.php?t=1306289") had a problem with adobe-flashplugin. I suggested he run the following commands. Maybe they can help you.

```
$ sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm  # Deletes a troublesome config file
$ sudo dpkg-reconfigure adobe-flashplugin --force  # Force-reconfigures adobe-flashplugin
$ sudo dpkg --purge --force-all adobe-flashplugin  # Force-removes adobe-flashplugin
$ sudo apt-get install flashplugin-nonfree  # Installs flashplayer the easy way
```

Good luck!

---

### Post by zdunham on 2009-10-30
Thanks very much for the replies! I bookmarked both of those links that you guys gave me in case it starts malfunctioning again but it seems to suddenly be working all the time.

---

