---
title: "didn't configure dhcp during install.....now problems"
date: 2006-05-08
forum: General Help
---

### Post by Xploit on 2006-05-08
Alright guys, as the title states, I didn't configure dhcp during my kubuntu install, cause I figured I could do it later, but Now I can't get any internet wired or wireless (Dell E1505 laptop)

I tried:
sudo ifconfig eth0 up  -- and it doesn't do anything

I tried:
sudo ifup eth0 -- "ignoring unknown interface eth0=eth0"

I tried it via guid from network settings, first I had to tab over to the "administrator button" cause the screen wouldn't display it (it was somewhere off the screen).  Then when I clicked it and entered the password, it didn't do nothing.  Like it just went back to the screen where you have to hit the "administrator button". 

So I logged off and did a console login as root and then typed "startx" to get me back into kde.  Then I went into network settings and I could hit the eth0 enable button, but when I did that, it enabled for like half a second and then disabled.  So no matter how many times I pressed the button, it wouldn't enable.

I have a feeling this could be related to not configuring dhcp during the install process.  Can anyone please help me out here.

Thanks a lot.

---

### Post by louis_nichols on 2006-05-08
No, man! It shouldn't matter. I don't use KDE right now, but I remember having a similar problem with the GUI.

Try it the old-fashion way:

1. First, make a backup of the file we'll dit:

```
sudo cp /etc/network/interfaces /etc/network/interfaces.backup
```
2. Open it for editing

```
sudo gedit /etc/network/interfaces
```

3. Now, in this file you should add this line:

```
iface eth0 inet dhcp
```

4. Now try to start it: ```
sudo ifup eth0
```

and, if things go well it should just work. If it doesn't, please post here the contents of your /etc/network/interfaces file.

---

### Post by Xploit on 2006-05-08
Worked like a charm man, thank you.

---

### Post by louis_nichols on 2006-05-08
glad to hear it! :) you're wellcome!

---

