---
title: "!!!!!HELP. I messed my ubuntu. HELP!!!!! something in compiz"
date: 2010-06-05
forum: General Help
---

### Post by aarondewindt on 2010-06-05
I was experimenting whit the compiz config maneger when suddently when I changed a setting and the screen went black whit some white parts. 

I restarded And th problems apear again when the windows where I enter my password for the network connection closes or After that I click on something else.


The setting I was changing was in the window blurr or something like this. and it apear when I checked a checkbox by focus blurr I think. The window blurr was already activated.

I cannot do anything form ubuntu. Whit the black screen I don;t know where to click. But I know I clic on things because of the position of the white parts. They change by the position of the windows.


I think that I need to deactivate compiz or atleast that plugin from the recovery mode. But I don;t have any idea how to do that. I don;t want to reinstall. I have some important files in there.


I am using ubuntu 8.10.

I have also KDE installed, I know that KDE does not use Compiz so I think I could change the setting back from KDE. The problem is that I made it login automatecaly to GNOME.


!!!!!!!!!! Please help me !!!!!!!!!!


NOTE: sorry for all the orthografy and gramatical error's in the tread. I don;t speak Inglish and I'm nervus.

OTHER NOTE: I am new to ubuntu. I installed it in 2008 but I have only some moths (2 or 3) experimenting with it.

Is there somewhere else I could ask for more help whith this?

---

### Post by XubuRoxMySox on 2010-06-05
You say you don't want to re-install Compiz, but the Compiz settings - the ones you messed up - have to be removed or repaired. Since you're new to Ubuntu, believe me it is so very much easier to just *completely remove* Compiz and re-install it from Synaptic, then do your settings again - carefully this time - than it is to try to figure out what you did wrong and what files to edit.

If it were me, I would log into KDE, **open Synaptic**, find **Compiz**, Compiz-fusion, and anything else with compiz in it's name and **Mark for Complete Removal**, then click **Apply**. When it's finished, simply let Synaptic refresh, then find Compiz again and **Mark for Installation**. Starting over is a whole lot easier.

Been there too,
Robin

---

### Post by aarondewindt on 2010-06-07
The problem is that I cannot enter KDE, because I cannot log out from the gnome, beacause the screen becomes almost completly black and I don;t know where to click.

If some one could send me some screen shots to see where the buttons are locadet and so I can log out and go to the login screen.

Or how can I get to the login screen from the recovery mode?

---

### Post by SlidingHorn on 2010-06-07
> **dixiedancer said:**
> You say you don't want to re-install Compiz, but the Compiz settings - the ones you messed up - have to be removed or repaired. Since you're new to Ubuntu, believe me it is so very much easier to just *completely remove* Compiz and re-install it from Synaptic, then do your settings again - carefully this time - than it is to try to figure out what you did wrong and what files to edit.

If it were me, I would log into KDE, **open Synaptic**, find **Compiz**, Compiz-fusion, and anything else with compiz in it's name and **Mark for Complete Removal**, then click **Apply**. When it's finished, simply let Synaptic refresh, then find Compiz again and **Mark for Installation**. Starting over is a whole lot easier.

Been there too,
Robin

Couldn't the OP also do:

```
sudo apt-get remove --purge compiz-fusion
```

or would that take some gnome-necessary files with it?

---

### Post by RyanBrown82 on 2010-09-04
I did the same thing...well sort of.
 
I have docky installed on 10.04. I clicked my widget layer box in Compiz and everything dissapeared. My desktop shows up but no menus or files. I can see the text from my dock but no graphix. I tried using hotkeys to access the terminal, but I cant see it. I think it's all open. I can press some keys and some windows will pop up but then dissapear quickly. I can't do anything. Please Help.
 
I think my whole desktop is set to a widget layer...or something like that. 
 
When I reboot it still does the same thing. I also have my comp set to auto log in, so I can't access the log in screen either.
 
HP netbook. 
Ubuntu 10.04
Docky
Compiz
 
sorry if this is in the wrong forum or thread... I don't know how these things work. (and find them very complicated to use.)

---

### Post by krimzonstarr on 2010-09-05
If you cannot even login due to the graphic problem, when the user selection/password (gdm) screen loads, Press Ctrl-Alt-F1. *startEdit* Since you are set to auto-login, this should still work even once you are in Gnome *endEdit* This will load a CLI, login normally there. At that point, you can run

```
sudo apt-get purge compiz*
```

That will remove all the compiz apps and extentions. To reboot from the CLI, use

```
sudo reboot now
```

Hopefully, you will be able to login after a reboot without the graphical problems!

---

