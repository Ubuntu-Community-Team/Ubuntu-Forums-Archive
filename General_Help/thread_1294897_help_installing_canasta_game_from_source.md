---
title: "help installing canasta game from source"
date: 2009-10-18
forum: General Help
---

### Post by timzak on 2009-10-18
Hi all,

I'm trying to install this game:

[http://linux.softpedia.com/get/GAMES-ENTERTAINMENT/Puzzle/Canasta-46683.shtml](http://linux.softpedia.com/get/GAMES-ENTERTAINMENT/Puzzle/Canasta-46683.shtml)

It seems like there is no installer.  I've googled my eyes out, so it seems it needs to be installed from source.  Could someone help me do this in Jaunty 64-bit?

edit: It doesn't have to be this particular game.  I'm looking for a Canasta game for Ubuntu.  I'd prefer one with a deb, ppa or other easy to install method.  This happens to be the only linux version I could find.

Thanks,
Tim

---

### Post by timzak on 2009-10-18
Huh?

Sorry if I've done something wrong.  I just want to be able to install and play this game and there's no easy way of doing so.

---

### Post by timzak on 2009-10-19
Any help greatly appreciated.

---

### Post by aftermgates on 2009-10-19
Is it installing from source that you need help with?
See if this helps [https://help.ubuntu.com/community/CompilingEasyHowTo]("https://help.ubuntu.com/community/CompilingEasyHowTo")

---

### Post by mark44magnum on 2009-10-19
i too would like some help installing this game, so any help would be great.mark
p.s. i have had a look at the website aftermgates pointed timzak too but it wasn't much help.

---

### Post by P4man on 2009-10-19
You **dont** need to compile the game, as its written in python.

However it seems to depend on a package called python-pygame. Install that using synaptic or by typing:

```
sudo apt-get install python-pygame
```

Then extract the canasta tarball somewhere (say on your desktop). Open a terminal, change directories to where you extracted it. for instance:

```
cd Desktop/canasta-0.2.5
```

Then launch it with

```
python Canasty.py
```

---

### Post by mark44magnum on 2009-10-19
thanks for the help but it still won't start, keeps telling me no module named twisted.internet.:(

---

### Post by P4man on 2009-10-19
can you copy paste the exact output ?

---

### Post by mark44magnum on 2009-10-19
hi, thanks for the help, here is the output.

Traceback (most recent call last):
  File "Canasty.py", line 10, in <module>
    from twisted.internet import reactor
ImportError: No module named twisted.internet

---

### Post by P4man on 2009-10-19
looks like another missing dependency. Try this:
```
sudo apt-get install python-twisted
```

---

### Post by mark44magnum on 2009-10-19
thank you for you help, it works like it should,is there any way to make a shortcut so i don't have to open a terminal cd to the folder and run canasty.py each time??   thank you again for your time and help..mark:P:P

---

### Post by P4man on 2009-10-19
You could create a little script. Create a new file and paste this in it:
```

#!/bin/bash
cd /home/username/path/to/game && python Canasty.py
```

(obviously correcting path and username)

Save it, right click it, properties and make it executable.

Perhaps there is an easier way, but im not sure how else to set a working directory in a launcher.

---

### Post by timzak on 2009-10-19
Thank you, P4man!

Got it working.

Regards.

---

