---
title: "graphic driver deleted - reinstall via CL how to???"
date: 2010-09-12
forum: General Help
---

### Post by goetzendorf on 2010-09-12
Dear folks,

this qualifies for an emergency call: 

DELL XPS 
NVIDIA GEForce Go 8600 M GT
Ubuntu 10.04.1 up to date installed

I obviously have accidentally deleted the graphic drivers & setting

System start ends at a message 'graph mode too low' - after using every option offered - I am ending up at the command line.

I'm using the Live-CD to make this request:

My question: is it possible to reinstall this graph-driver from CL and how??

I'm new to Ubuntu.

Is there somebody out there willing to give me a Dummy version of advice?
I need a running OS tomorrow as I'm using this laptop for work.

Many thanks in advance an best regards
Christian

---

### Post by kamicc on 2010-09-12
```

wget http://us.download.nvidia.com/XFree86/Linux-x86/256.53/NVIDIA-Linux-x86-256.53.run
sudo sh ./NVIDIA-Linux-x86-256.53.run

```

? :)

---

### Post by WorMzy on 2010-09-12
```
sudo apt-get install nvidia-current && nvidia-xconfig
```

---

### Post by goetzendorf on 2010-09-13
Dear Karmicc,
Dear WorMzy,

thank you both for your advice. Both worked...in some way, but I wasn't able to solve the problem.

In case of interest, the whole story:

After re-installing Lucid I discovered the crucial reason: when I tried to [COLOR="Red"]de-install pulseaudio again: last topic in the line of dependencies to be deleted: Ubuntu-desktop !!!![/COLOR]

To my view a monstrous bug.

As additionally the backup programm produced only emtpy folders, I have lost:

6 hours of work and all my files

Sorry but thats that, I will return to Vista again.

Best regards

---

### Post by WorMzy on 2010-09-13
That is, in my opinion, the main fault with Ubuntu; if Canonical decide you should use a certain application, then they make it a false dependency that the whole desktop relies on, just so that you can't remove it. Personally, I find that obtrusive, unfriendly, and pretty underhanded, and is the main reason why I use Arch Linux these days.

But still, you didn't lose any of your files by removing ubuntu-desktop or the related applications; your /home folder will have been untouched by the process. Mounting your windows partition (or plugging in a USB drive) would provide you with a place to copy the contents of your /home folder, safely backing everything up before a reinstall, or partition removal if that is your decision.

---

### Post by realzippy on 2010-09-13
*To my view a monstrous bug...*

Yes,there should be a big fat warning sign.Many fresh users run in the "synaptic deinstall trap.."
Boot in recovery mode and reinstall ubuntu-desktop...

---

