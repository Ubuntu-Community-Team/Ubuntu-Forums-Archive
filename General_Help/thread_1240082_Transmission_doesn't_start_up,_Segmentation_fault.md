---
title: "Transmission doesn't start up, Segmentation fault"
date: 2009-08-14
forum: General Help
---

### Post by fatigue on 2009-08-14
I use Ubuntu 8.10

Recently I installed Vuze and I uninstall vuze.
Since then, Transmission have not started up. 

This is what i did. I uninstall transmission completely. Restart my pc.
I used, apt-get install clean and apt-get autoclean
and then
I installed trasmission through terminal, sudo apt-get install transmission

However, transmission doesn't start up. When i type transmission,
i get this message.
"
Segmentation fault"

also i went home/usr/  and list hidden folder.   I cannot find .transmission  

Could you guys help me with this?

---

### Post by GoldenSun on 2009-08-14
try a purge command
```

sudo aptitude purge transmission

```

then try re-installing it.

Or try out a different torrent client, like deluge.

---

### Post by fatigue on 2009-08-14
thank you for help!
But it didnt work:( I guess ill have to use other client.

---

### Post by Sidewinder1 on 2009-08-14
Perhaps:
```
sudo aptitude purge vuze
```
Not sure this'll accomplish the task but I don't think it'll hurt since you already removed it...
Side

---

### Post by fatigue on 2009-08-14
That didnt work as well.
Is this bug of transmission?

---

### Post by Charles Kerr on 2009-08-15
> **fatigue said:**
> That didnt work as well.
Is this bug of transmission?

This sounds like maybe one of your configuration files has been corrupted.  You might try moving (or backing up then deleting) your $HOME/.config/transmission folder, which will effectively wipe all your Transmission settings so that you can start with a clean slate.

If Ubuntu pops up a crash dialog when Transmission gets a segmentation fault, please use the Ubuntu crash tool to file a bug report in Launchpad.  It's got all kind of automated reports that can help the programmers to track down bugs.

---

### Post by fatigue on 2009-08-15
> You might try moving (or backing up then deleting) your $HOME/.config/transmission folder

THIS FIXED IT!!

Basiaclly home/.config/transmission was corrupted. I deleted this folder and start transmission. WORKED!
THANK YOUl

---

### Post by Charles Kerr on 2009-08-15
(edit: erasing duplicate post)

---

