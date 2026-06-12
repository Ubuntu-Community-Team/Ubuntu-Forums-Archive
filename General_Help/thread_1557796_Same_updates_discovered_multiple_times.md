---
title: "Same updates discovered multiple times"
date: 2010-08-21
forum: General Help
---

### Post by veggen on 2010-08-21
At first, I was ignoring this strange occurrence, but it's become quite bothersome now.
My Update Manager keeps finding and installing same updates over and over. For example, it updated Wine to 1.2 at least 4 times. Kernel was updated to 2.6.32-24 at least thrice.
I checked for updates just now and it only found language packs. But after installing those, I rechecked, and again it found kernel 2.6.32-24!

What gives? Does this happen to everyone? Do all these duplicated updates take additional space or do they get written over each other?
Any ideas how I might solve this?

---

### Post by dino99 on 2010-08-21
its time to look closely to your synaptic repo tab: clean it

you might want to clean the sources too:
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

note: wine is 1.3.0 now (and be 1.3.1 in few hours

---

### Post by veggen on 2010-08-21
Thanks for the prompt response!
I did all the clean-up commands (everything's the same, I still got kernel 2.6.32-24 listed), but I didn't really understand what did you mean by cleaning my synaptic repo tab...

In case it's useful to know, I have the following sources enabled:
main, universe, restricted, multiverse,
archive.canonical.com/ubuntu lucid,
deb.opera.com/stable,
deb.playonlinux.com/ lucid,
ppa.launchpad.net/anyremote/ppaubuntu lucid,
ppa.launchpad.net/ubuntu-wine/ppaubuntu lucid

And the following updates checked:
lucid-security, lucid-updates, lucid-backports

[color=red][EDIT][/color]
Sorry. I just realized the version of kernel has actually changed on the last digit (which only shows in the details). I guess the same thing happens with some other packages.

Sorry for the inconvenience, and thanks again.

---

### Post by jmfal on 2010-08-21
If you have a ppa repo you should put a ckeck in the sources box in software sources
 
Are you using the update manager in ubuntu tweak, and original update manager?

I accidentally enabled the ubuntu tweak-update man and that is what happened to me ,

Go to ubuntu tweak and uncheck the two boxes at the bottom of the update manager section , this should solve  the problem

---

