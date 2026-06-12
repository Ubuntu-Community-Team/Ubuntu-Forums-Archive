---
title: "upgrade just wiped out about 30 programs whats up with that"
date: 2012-04-18
forum: General Help
---

### Post by Bushcraft Bill on 2012-04-18
I was intently working on a project then the system wanted to do an update so I let it then it asked me if I wanted it to delete some no longer needed programs I though that it would be some of the ubuntu core programs nope it wiped out over 30 programs gone and now I it wont even let me install them again I really need kdenlive or openshot they will not install at all or skype I need these programs is their anyway to go back intime and undue this last update that has hosed me so bad...

if this is the way ubuntu is going to do things in the future I am better off going back with windows at least it does not delete programs I just think this is totally unexceptible to me that ubuntu wiped out so many programs on me....

Right now I am so hooped/screwed what do I need to do to get ubuntu to let me install programs again?

---

### Post by dragonfly41 on 2012-04-18
This might give you a history of your installations .. to help reinstall

gksu gedit ~your_user_name/.bash_history

---

### Post by Bushcraft Bill on 2012-04-18
Thanks tried it and got this: 

(gksu:4522): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

and thier was nothing in the files it opened up...


> **dragonfly41 said:**
> This might give you a history of your installations .. to help reinstall

gksu gedit ~your_user_name/.bash_history

---

### Post by Bucky Ball on 2012-04-18
What release are you using? Could you check also in System Monitor?

---

### Post by wojox on 2012-04-18
> **dragonfly41 said:**
> This might give you a history of your installations .. to help reinstall

gksu gedit ~your_user_name/.bash_history

```
gedit ~/.bash_history
```
Is how you would edit that. Anyway there is nothing in there to tell you what happened. It just remebers the commands you use.

---

### Post by Bushcraft Bill on 2012-04-18
just tried to manualy install and this is what I got

I am using 11.10 no idea what this last update did though to that

sudo apt-get install openshot
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 openshot : Depends: python-mlt3 but it is not going to be installed or
                     python-mlt2 but it is not installable or
                     python-mlt but it is not installable
E: Unable to correct problems, you have held broken packages.

---

### Post by Bushcraft Bill on 2012-04-18
ya its just a history of what programs I have tried to install did get it working with your commands you posted thanks...


> **wojox said:**
> ```
gedit ~/.bash_history
```
Is how you would edit that. Anyway there is nothing in there to tell you what happened. It just remebers the commands you use.

---

### Post by tmaranets on 2012-04-18
Try installing Ubuntu an wipe the old one of your disk. Then, install all of the programs that were wiped by the update.

---

### Post by Frogs Hair on 2012-04-18
Did you run an update or upgrade?  If you ran an upgrade from 11.04 to 11.10 there would be many programs that would not be compatible with 11.10 . 11.04 uses Gnome 2 and 11.10 uses Gnome 3.

---

### Post by oldfred on 2012-04-18
If you want to see if it is some command. At terminal just list the history with 

history

You may need to resync everything. 

#Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a


If you want to check logs, use log file viewer from system tools and look at dpkg.log. It should show everything installed. But it can be long.

---

### Post by lisanels47 on 2012-04-18
Package problems.  
First run "apt-get -f install" to solve unresolved things.  Then "apt-get update && apt-get -y dist-upgrade" to make sure it's up to date.  After that, there's no reason you shouldn't be able to install the packages you want unless you have manually installed something that interferes with the package manager.

---

### Post by Bushcraft Bill on 2012-04-18
I did your stuff I think that helped out Thanks _oldfred_! but I still have a problem with installing openshot but have found this info how do I resolve this?
I am assuming I have to install this package what command do I use to install this?

The following packages have unmet dependencies:

openshot: Depends: python (>= 2.5) but 2.7.2-7ubuntu2 is to be installed

---

### Post by oldfred on 2012-04-18
Is it really saying python to be installed. Major parts of Ubuntu have to have the default version of python. Did it get uninstalled? Or did you attempt to  install only python3?

sudo apt-get install python

The logic it says says 2.5 or greater, so 2.7 should be ok.

---

### Post by Bushcraft Bill on 2012-04-19
the update changed something but I did that command and got this: python is already the newest version.
could it just be that openshot does not like the latest version of python then? thats my thinking right now....

I got just about everything else I desperately needed working again so I am a happy camper once again, openshot is the only problem I have now....

again thanks for your help....



> **oldfred said:**
> Is it really saying python to be installed. Major parts of Ubuntu have to have the default version of python. Did it get uninstalled? Or did you attempt to  install only python3?

sudo apt-get install python

The logic it says says 2.5 or greater, so 2.7 should be ok.

---

