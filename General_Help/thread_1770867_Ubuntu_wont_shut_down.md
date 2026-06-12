---
title: "Ubuntu wont shut down"
date: 2011-05-29
forum: General Help
---

### Post by TimEnid on 2011-05-29
Every time i shut down my PC, i get a message saying Ubuntu one is still open, and syncing. I don't even use this. How can i prevent this from happening.

---

### Post by webofunni on 2011-05-29
Try 

```

sudo apt-get purge ubuntuone-client-gnome

```

---

### Post by TimEnid on 2011-05-29
that didn't work

---

### Post by linuxinstalledfromhdd on 2011-05-29
Try cleaning your configuration settings and your entire system.

I recommended 

sudo apt-get install bleachbit
sudo bleachbit

Careful, don't let it delete your passwords and bookmarks. 

Next thing you can do is install Ubuntu-Tweak, and use the package cleaner.
That helps get most of the junk off there you don't need anymore.

and run

sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get clean all

Reboot it.

---

### Post by TimEnid on 2011-06-05
> **linuxinstalledfromhdd said:**
> Try cleaning your configuration settings and your entire system.

I recommended 

sudo apt-get install bleachbit
sudo bleachbit

Careful, don't let it delete your passwords and bookmarks. 

Next thing you can do is install Ubuntu-Tweak, and use the package cleaner.
That helps get most of the junk off there you don't need anymore.

and run

sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get clean all

Reboot it.
tried this as well. it still happens.

---

### Post by webofunni on 2011-06-06
paste the o/P of

```

ps aux | grep -i ubuntuone

```

---

### Post by linuxinstalledfromhdd on 2011-06-06
Open synaptic package manager and remove all instances of Ubuntu One from your system.  Back up your system prior to doing this, and you should be fine.

---

### Post by miasmablk on 2011-06-06
open terminal and create a super user password

```
sudo passwd
```

enter your desired password.

now alt + ctr l+ f2

type your user name, then password

then enter ```
sudo shutdown -h 1
```

enter password. computer should shutdown in one minute.

---

