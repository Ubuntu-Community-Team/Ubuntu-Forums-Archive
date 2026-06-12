---
title: "Can't connect to Cups server after update"
date: 2010-06-27
forum: General Help
---

### Post by acidblue on 2010-06-27
After a recent software update I can no longer connect to the Cups server.
My printer isn't listed anymore and won't let me add one.
Cups was listed in the update so i think the update broke cups.
I'm getting: "Failed to connect to server" when i try to connect to 'localhost'.
What can I do?

10.04 Lucid 64 bit.

---

### Post by piccolinux on 2010-06-28
Look at this, may be it helps you:

[http://swiss.ubuntuforums.org/showthread.php?t=1475058](http://swiss.ubuntuforums.org/showthread.php?t=1475058)

---

### Post by acidblue on 2010-06-28
Thanks for link.
A simple:```
sudo /etc/init.d/cups restart
```

Seems to have done the trick.

---

### Post by psychlic on 2010-07-11
> **acidblue said:**
> Thanks for link.
A simple:```
sudo /etc/init.d/cups restart
```

Seems to have done the trick.

It just worked for me, thanks acidblue :D I have an assignment due on Wednesday and not being able to print was a bit of a problem.

---

### Post by Mintux on 2010-08-14
I have the same problem, only it keeps reappearing after reboot and it's a bit annoying to have to restart CUPS every time. 

Any suggestions for a more permanent fix?

---

### Post by Morbius1 on 2010-08-14
**[1]**  The first thing you should look at is if the following file is empty:
> /etc/network/interfacesIt should have the following content:
> auto lo
iface lo inet loopback
**[2]**  If that's not the issue then create a little script that will force a start on every boot:

Create a script:
```
gksu gedit /etc/network/if-up.d/cups 
```With this content:
```
#!/bin/sh
service cups restart 
```Save the file and make it executable:
```
sudo chmod +x /etc/network/if-up.d/cups 
```Reboot

---

