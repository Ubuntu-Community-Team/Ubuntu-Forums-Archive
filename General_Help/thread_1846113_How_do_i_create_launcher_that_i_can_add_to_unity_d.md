---
title: "How do i create launcher that i can add to unity dock when running compiz?"
date: 2011-09-18
forum: General Help
---

### Post by Pampanga on 2011-09-18
I want to create a launcher for my wow.exe (runs in wine) that i can add to unity dock. I don't know how to do it under compiz...most of the tutorials to create one such as here [http://www.youtube.com/watch?v=_17xBc0p90s](http://www.youtube.com/watch?v=_17xBc0p90s) for example, dont use compiz (which doesn't allow pinning icons or files on the desktop). Anyone know a simpler way to do this? or shall I just turn compiz off, follow the above link and hope that it works.

I would appreciate any help...Thanks

---

### Post by wildmanne39 on 2011-09-18
Hi, here is a link for creating launchers and many other things, you will need to scroll down the page a little.
[http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity](http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity)
Thank you

---

### Post by fishbulb1022 on 2011-09-19
The best way I know is to create a new .desktop launcher in your /usr/share/applications folder. You can copy a launcher for another program and change the command and icon. It's very simple, but if you need help. I sent in a tip to omgubuntu and they posted it here: [http://www.omgubuntu.co.uk/2011/07/unity-launchers-compiz-plugins/]("http://www.omgubuntu.co.uk/2011/07/unity-launchers-compiz-plugins/"). It's for creating a launcher for the scale plugin in compiz, but you should be able to extrapolate the relevant material pretty easily.

---

### Post by Pampanga on 2011-09-30
Thank you very much fishbulb1022. What I did was I copied a launcher from  my /usr/share/application folder (in this case I copied the Mangler  launcher but any launchers will do) and paste it in the desktop folder. I  changed the icon, and in the "Command" section I put: 
        wine /home/pampanga/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe    

Double clicked to launched wow, once it's running, right clicked the wow icon in Unity dock and selected "Keep In Launcher"
Worked like a charm!!
CHEERS! :guitar:

---

### Post by wildmanne39 on 2011-09-30
Hi, your welcome! I am glad you have it working.

---

### Post by Krytarik on 2011-09-30
> **Pampanga said:**
> What I did was I copied a launcher from  my /usr/share/application folder (in this case I copied the Mangler  launcher but any launchers will do) and paste it in the desktop folder. I  changed the icon, and in the "Command" section I put: 
        wine /home/pampanga/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe    

Double clicked to launched wow, once it's running, right clicked the wow icon in Unity dock and selected "Keep In Launcher"
Just something to consider: By doing it that way, you are going to lose your launcher in the dock, if you delete the one on your desktop. So, better use "~/.local/share/applications" as the 'source' for your dock launchers.

In your case, after creating the launcher on your desktop, either move or copy it to that location in your home directory, and then drag & drop it into your dock from there.

Greetings.

---

### Post by Pampanga on 2011-10-07
> **Krytarik said:**
> Just something to consider: By doing it that way, you are going to lose your launcher in the dock, if you delete the one on your desktop. So, better use "~/.local/share/applications" as the 'source' for your dock launchers.

In your case, after creating the launcher on your desktop, either move or copy it to that location in your home directory, and then drag & drop it into your dock from there.

Greetings.


You are absolutely right. Thank you very much...did exactly as you said...:D

---

