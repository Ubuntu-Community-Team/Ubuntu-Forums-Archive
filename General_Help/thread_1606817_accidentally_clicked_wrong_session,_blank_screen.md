---
title: "accidentally clicked wrong session, blank screen"
date: 2010-10-27
forum: General Help
---

### Post by Yondergod22 on 2010-10-27
Posted this in the wrong section so I'm reposting it, is that ok?

I installed lxde and logged out and switched to it, but my internet wasn't working (but that's a different thread after I fix this, I was going to try installing wicd) So I tried to go back to gnome, I misclicked and accidentally started a different session. I think it said openbox/gnome, all I get is a blank screen with just the desktop background. It's set to automatically log me in, so when I restart my computer it goes back to the blank screen. How do I get back to the login screen?

Thanks in advance

---

### Post by sisco311 on 2010-10-27
Switch to a virtual console (Ctrl+Alt+F2) and log in. If you are using lxdm as your default display manager, edit the /etc/lxdm/default.conf and comment out the **autologin** line:
```
sudo nano /etc/lxdm/default.conf
```
```
[base]
**#** autologin=username
...
```
Press Ctrl+x, y, Enter to save the file and exit.

Restart lxdm:
```
sudo initctl restart lxdm
```

If you are using GDM, edit /etc/gdm/custom.conf and set the value of **AutomaticLoginEnable** to **false**.

Restart gdm:
```
sudo initctl restart gdm
```



Oh, and you can use the [IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG] button to ask a moderator to move your thread...

---

### Post by drs305 on 2010-10-27
This thread remains since it has had a response. The other thread has been removed.

---

### Post by Yondergod22 on 2010-10-27
Thak you very much Sisco, it worked :)
And sorry I'm blind I looked everywhere except where it is for the report button...

Thanks for deleting my other thread Drs

---

### Post by sisco311 on 2010-10-27
My pleasure!

---

