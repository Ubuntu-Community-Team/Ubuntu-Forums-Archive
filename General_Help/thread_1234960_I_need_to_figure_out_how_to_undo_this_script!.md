---
title: "I need to figure out how to undo this script!"
date: 2009-08-08
forum: General Help
---

### Post by Austin 'D' King Wehmeyer on 2009-08-08
[COLOR=Blue]Ok so I followed this tutorial,[COLOR=Red]http://ubuntuforums.org/showthread.php?t=50814[/COLOR]5 which did not work I ran the command and the script opened and i put in the new command in the script and click save, now I have found out that i can just enable internet connection sharing in Ubuntu via ipv4 settings, so I think this script is messing thing up and i need to know how i can undo it? Thanks every one, and please keep replys noobis[/COLOR]h :D

---

### Post by cariboo on 2009-08-08
IF you edited /etc/rc.local, then just remove what you added to the file. Press Alt-F2 and type:

```
gksu gedit /etc/rc.local
```

You may have to flush the iptables rule:

```
iptables -F
```.

Then restart networking:

```
sudo /etc/init.d/networking restart
```

---

### Post by Austin 'D' King Wehmeyer on 2009-08-08
[COLOR=Blue]Thanks! I got it!
[/COLOR]

---

