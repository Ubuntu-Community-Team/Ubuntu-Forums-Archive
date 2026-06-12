---
title: "flash plugin for Firefox"
date: 2009-11-28
forum: General Help
---

### Post by Lofnes on 2009-11-28
Please can anyone help before I do more damage. I am very new to Ubuntu and among the first things that I tried to do was to download Flash. The download was unsuccessful but it has blocked up all my downloads and updates. I cannot uninstal it and get a message that it is so unstable that the program should be reinstalled. I can neither instal nor remove from the system. I have tried all the suggestions I have found in the forums but they have been unsuccessful. I am at a loss what to do now.

---

### Post by john newbuntu on 2009-11-29
I am assuming "adobe-flashplugin" is the name of the package.  What does typing this on a terminal give you?
sudo apt-get remove adobe-flashplugin

---

### Post by Xeostar on 2009-11-29
Hi,

I think I've got the same issue. I get the error:-

E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.

???

Xeostar :KS

---

### Post by john newbuntu on 2009-11-29
Your solution is probably in this external thread:
[http://sidux.com/PNphpBB2-viewtopic-t-17624.html](http://sidux.com/PNphpBB2-viewtopic-t-17624.html)

---

### Post by Leppie on 2009-11-29
Have a look at the [media guide]("http://ubuntuforums.org/showthread.php?t=766683&highlight=media+guide").

The troubleshooting part covers adobe-plugin issues (I solved mine using this guide).

---

### Post by wojox on 2009-11-29
```

#Remove Flash
sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm  # Deletes a troublesome config file
sudo dpkg-reconfigure adobe-flashplugin --force  # Force-reconfigures adobe-flashplugin
sudo dpkg --purge --force-all adobe-flashplugin  # Force-removes adobe-flashplugin
sudo apt-get install flashplugin-nonfree  # Installs flashplayer the easy way


```

---

### Post by Lofnes on 2009-11-29
> **wojox said:**
> ```

#Remove Flash
sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm  # Deletes a troublesome config file
sudo dpkg-reconfigure adobe-flashplugin --force  # Force-reconfigures adobe-flashplugin
sudo dpkg --purge --force-all adobe-flashplugin  # Force-removes adobe-flashplugin
sudo apt-get install flashplugin-nonfree  # Installs flashplayer the easy way


```

thank you so much. My problem seems to have been removed

---

### Post by Lofnes on 2009-11-29
> **wojox said:**
> ```

#Remove Flash
sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm  # Deletes a troublesome config file
sudo dpkg-reconfigure adobe-flashplugin --force  # Force-reconfigures adobe-flashplugin
sudo dpkg --purge --force-all adobe-flashplugin  # Force-removes adobe-flashplugin
sudo apt-get install flashplugin-nonfree  # Installs flashplayer the easy way

```

Thank you Wojox. It solved my problem after a week of worrying.

---

### Post by carl_pr on 2009-11-29
wow today i wanted to try kubuntu to see KDE for the first time and im having this same problem when i tried to install flash, i suppose the same commands will work on KDE right? im not right now at home so i cant try it. Ill check it out later, hope this solve my issue too cuz it pissed me off.

---

### Post by Xeostar on 2009-11-29
Chaps,

Thanks form me too that bit of code did the trick, I've no idea what tricks it did but it worked :p.

Xeostar

---

### Post by carl_pr on 2009-11-29
anyone knows if this same solution works with Kubuntu? I am having this issue on kubuntu and i suppose the poster is using ubuntu. I dunno if this would work  on kubuntu.

---

### Post by wojox on 2009-11-30
Yes, just open konsole and enter those commands

---

