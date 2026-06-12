---
title: "Animations not showing up in CCSM after installing theme."
date: 2011-08-01
forum: General Help
---

### Post by BladeTec on 2011-08-01
Hi,

Yesterday, I installed a new theme for my laptop (Ubuntu 11.04(32-bit)) and soon after, I noticed that the animations I set up were not showing up anymore. Before the installation, everything worked fine. The theme is called MacBuntu 11.04. (Not the original one)

Here is a picture:
[IMG]http://i1209.photobucket.com/albums/cc385/gmdeus/ccsm.png[/IMG]

Need more info ? Don't hesitate to ask.

Thanks in advance,
Mark.

---

### Post by BladeTec on 2011-08-01
BUMP ! Please, I could really use some help here :)

**Edit**
I know bumps are annoying, but please :\

---

### Post by BladeTec on 2011-08-01
Up ! Come on, anyone... :(

---

### Post by kcraptor82 on 2011-08-01
Don't feel bad, I have the same problem. After I installed the macbuntu them my compiz was messed up on my server box. My laptop I got everything working almost perfect so I just copied my settings from it, well now I have no animations, well I never did to begin with, but still, wtf? Mine looks the same also!

---

### Post by BladeTec on 2011-08-02
Alright, so we are 2 now... Anyone can help ?

---

### Post by BladeTec on 2011-08-02
Alright, so I knwo I'm not supposed to bump that much, but we are not getting any help. Please, anyone ?

---

### Post by lkjoel on 2011-08-02
Type this into a Terminal window:
```
sudo apt-add-repository ppa:lkjoel/apt-undo
sudo apt-get update
sudo apt-get install apt-undo
apt-undo purge compiz compiz-core compizconfig-settings-manager compizconfig-backend-gconf compiz-gnome compiz-plugins-default compiz-plugins-main-default compiz-kde compiz-fusion-plugins-extra compiz-plugins-extra
apt-undo undo
```
Then reboot

---

### Post by BladeTec on 2011-08-02
@lkjoel

Did what you said, but still nothing... :|

Thanks a lot for the help though. Are there any other solutions ?

---

### Post by lkjoel on 2011-08-02
Could you give me the output of the commands?

---

### Post by BladeTec on 2011-08-03
@lkjoel

Here it is. Looks normal though.

```
mark@Mark-Laptop:~$ apt-undo purge compiz compiz-core compizconfig-settings-manager compizconfig-backend-gconf compiz-gnome compiz-plugins-default compiz-plugins-main-default compiz-kde compiz-fusion-plugins-extra compiz-plugins-extra
[sudo] password for mark:  

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package compiz-plugins-default
E: Unable to locate package compiz-plugins-main-default
Creating undo data ... 
To undo: bash /home/mark/.aptundo/2011/08/03/20110803125142
mark@Mark-Laptop:~$ apt-undo undo
mark@Mark-Laptop:~$ 

```

---

### Post by lkjoel on 2011-08-03
Some packages were not found. Try this instead:
```
apt-undo purge [compiz]("http://en.wikipedia.org/wiki/Compiz") compiz-core compizconfig-settings-manager compizconfig-backend-gconf compiz-gnome compiz-kde compiz-fusion-plugins-extra compiz-plugins-extra
apt-undo undo

```

---

### Post by kcraptor82 on 2011-08-04
Well since I am having the same problem, but I am sorta lost here. If I use your commands, won't it remove compiz fuse? 

raptor@main:~$ apt-undo purge compiz compiz-core compizconfig-settings-manager compizconfig-backend-gconf compiz-gnome compiz-kde compiz-fusion-plugins-extra compiz-plugins-extra

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package compiz-kde is not installed, so not removed
The following package was automatically installed and is no longer required:
  mesa-utils
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  compiz* compiz-core* compiz-fusion-plugins-extra*
  compiz-fusion-plugins-main* compiz-gnome* compiz-plugins*
  compiz-plugins-extra* compiz-plugins-main* compizconfig-backend-gconf*
  compizconfig-settings-manager* fusion-icon* libcompizconfig0*
  python-compizconfig* ubuntu-desktop* ubuntu-tweak* unity*
0 upgraded, 0 newly installed, 16 to remove and 0 not upgraded.
After this operation, 31.4 MB disk space will be freed.
Do you want to continue [Y/n]? y

How does this solve our problem beside just removing the software that we want in the first place!

---

### Post by BladeTec on 2011-08-04
**EDIT**
I'm so stupid, I didn't see the above post by lkjoel... Sorry !

I'm going to try that.

---

### Post by BladeTec on 2011-08-04
@lkjoel ,

You sir honestly rock. That did the trick ! Thanks a bunch for your help !!!

P.S.:How can I mark it as solved ?

---

### Post by lkjoel on 2011-08-04
Glad it works! Thread tools->Mark this thread as solved.

---

### Post by kcraptor82 on 2011-08-05
Oh well never mind, I also did what you suggested, yes I was sorta worried, but it worked! your awesome, thank you so much!

---

