---
title: "Ubuntu repair"
date: 2010-12-25
forum: General Help
---

### Post by L Style on 2010-12-25
How to repair ubuntu without reinstalling.. please help me:confused:

---

### Post by susema on 2010-12-25
What's the matter? There're a lof of to do. Like, reseting panel, gnome settings or using fsck. &#304;f problem is your disk, you can use fsck with LiveCD.

```
sudo fsck /dev/sdaX
```

Where x = Your Ubuntu root partition number..

---

### Post by HermanAB on 2010-12-25
Two ways:
1. Research and fix the problem, using [http://google.com/linux](http://google.com/linux)
2. Re-install, without formatting the /home partition

If you don't have a separate /home partition, you now know why should always have one...

---

### Post by I'mGeorge on 2010-12-25
use your ubuntu installation disk that has the capabilities of being a Live CD either. But it all depends in what's broken, 'cause most of the problems can be solved just using the terminal with root privileges.

---

### Post by L Style on 2010-12-25
> **susema said:**
> What's the matter? There're a lof of to do. Like, reseting panel, gnome settings or using fsck. &#304;f problem is your disk, you can use fsck with LiveCD.

```
sudo fsck /dev/sdaX
```

Where x = Your Ubuntu root partition number..

Some pen drives doesn't work. After restarting Its work. And sometimes ubuntu freeze mouse and keyboard doesn't work. only solution is press restart button. I thought these problems solve after repair ubuntu. If you have good solution please help me.

---

### Post by matt_symes on 2010-12-25
Hi

> How to repair ubuntu without reinstalling.. please help me

Am i missing something here? 

What exactly is the problem with you Ubuntu installation?

Congratulations. That is the vaguest call for help i have ever seen. Provide details please.

Kind regards

---

### Post by L Style on 2010-12-25
> **L Style said:**
> Some pen drives doesn't work. After restarting Its work. And sometimes ubuntu freeze mouse and keyboard doesn't work. only solution is press restart button. I thought these problems solve after repair ubuntu. If you have good solution please help me.

bump

---

### Post by dino99 on 2010-12-25
you might check two things:

- driver activation: system admin additional driver
- errors logged:
 a) into .Xsession-errors (/home, ctrl+h to unhide it)
 b) into /var/log/: system admin logviewer

then run a few commands into a terminal:

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

---

