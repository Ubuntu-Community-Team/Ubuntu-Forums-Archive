---
title: "Windows emulators"
date: 2006-04-17
forum: General Help
---

### Post by Ob1 on 2006-04-17
How many are there, and which one is the best?

---

### Post by xXx 0wn3d xXx on 2006-04-17
[QUOTE=Ob1]How many are there, and which one is the best?[/QUOTE]
Wine. In terminal type:

> sudo apt-get install wine

Make sure to have the backports enabled.

---

### Post by PriceChild on 2006-04-17
There is also cedega, which you need to pay for, and plays quite a few of the latest games.

Crossover office. - speaks for itself.

There's vmware player and qemu which let you run windows inside of linux for free.

I've also seen something about parallel something or other, seems pretty new, does the same as vmware and qemu but you must pay for it.

---

### Post by Ob1 on 2006-04-17
[QUOTE=MasterChief1234]Wine. In terminal type:



Make sure to have the backports enabled.[/QUOTE]

hmm, what backports?

---

### Post by PriceChild on 2006-04-17
Take a look here:

[http://ubuntuforums.org/showthread.php?t=40291](http://ubuntuforums.org/showthread.php?t=40291)

---

### Post by Ramses de Norre on 2006-04-17
The backports repo ;)
```
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted
universe multiverse
```

---

### Post by Ob1 on 2006-04-17
Is there a list of what Windows programs that wine enables you to run?

---

### Post by xXx 0wn3d xXx on 2006-04-17
[QUOTE=Ob1]Is there a list of what Windows programs that wine enables you to run?[/QUOTE]
Not that I'm aware of, but it runs almost all windows applications and games.

---

### Post by localzuk on 2006-04-17
Wine Is Not an Emulator! :)

There are quite a few actual emulators though, such as vmware ([http://www.vmware.com](http://www.vmware.com) - the server and player versions are free), qemu (free and open source) and a few others that I can't remember the name of.

Wine, Cedega and the ilk are actually just API layers (they just map one systems commands onto the others - no actual emulation), so don't work (at the moment) perfectly - however when they do work, they generally work faster than an emulator.

---

### Post by localzuk on 2006-04-17
Yes. Take a look at [http://appdb.winehq.org](http://appdb.winehq.org)

---

### Post by localzuk on 2006-04-17
I'm afraid it doesn't. Not even close I'm afraid. There is good support for some applications but some just plain don't work (this applies to many games).

---

### Post by Ob1 on 2006-04-17
well the game that i am plaing to run is said to work with Wine or Xwine.

---

### Post by Ob1 on 2006-04-17
does it run the win apps properly?

---

### Post by xXx 0wn3d xXx on 2006-04-17
[QUOTE=Ob1]does it run the win apps properly?[/QUOTE]
It runs most windows app and games properly. However, I wouldn't recommend relying on wine to run windows apps. Try to find alternitives in Linux. Search in Synaptic.

---

