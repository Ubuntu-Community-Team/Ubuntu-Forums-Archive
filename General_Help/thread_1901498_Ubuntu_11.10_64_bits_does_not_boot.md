---
title: "Ubuntu 11.10 64 bits does not boot"
date: 2011-12-28
forum: General Help
---

### Post by drackololord on 2011-12-28
I am running an Acer Aspire X1200  [http://support.acer.com/acerpanam/desktop/0000/Acer/AspireX1200/AspireX1200sp2.shtml](http://support.acer.com/acerpanam/desktop/0000/Acer/AspireX1200/AspireX1200sp2.shtml)

with an only Operative system (No windows or another Distro) that is Ubuntu 11..10 64 bits Edition, the partition of it its Sda4 and the Sda1 its the linux-swap


Hello everyone yesterday i was having a little troubleshoot installing new virtual box version, did not uninstall it, and searching i find this command, already have been run it and nothing bad happens, its this 

```
sudo apt-get autoremove
```after it i just saw something about gnome, by by good luck id take a screenshot, lucky me, and it is this 

[http://www.flickr.com/photos/66277877@N08/6586104543/in/photostream](http://www.flickr.com/photos/66277877@N08/6586104543/in/photostream)

it was just 100 MB, don't remember doing anything else, turn it off and then, BLACK SCREEN :(:(:( :cry:
i dont see nothing, actually it gets black freezed screen, it doesnt beep or send me another type of command prompt

tried everything and nothing works, already found this

[askubuntu.com/questions/62640/after-apt-get-autoremove-missing-operating-system]("http://askubuntu.com/questions/62640/after-apt-get-autoremove-missing-operating-system")
everything as he says happens to me except it doesnt show anymore this text,

```
Missing Operating System.
```tried the solution he gave with my Live Cd Ubuntu 11.10 64 bits

```
sudo mount /dev/sda2 /mnt
``````
sudo grub-install --root-directory=/mnt /dev/sda 
```ans it shows me this

_[http://www.flickr.com/photos/66277877@N08/6589997027/in/photostream](http://www.flickr.com/photos/66277877@N08/6589997027/in/photostream)_

already try to repair broken packages with my cd using recovery mode pressing SHIFT or Esc and nothing, it shows me this, and gets freezed at this --Recovery Menu (limited read-only menu)--
try to remount and gets freezed so I cant repair brocken packages

[http://comments.gmane.org/gmane.linux.ubuntu.devel/34370](http://comments.gmane.org/gmane.linux.ubuntu.devel/34370)

what can i do

thanks you for anticipated

:confused:

---

### Post by oldos2er on 2011-12-28
Closed, duplicate here: [http://ubuntuforums.org/showthread.php?t=1901173](http://ubuntuforums.org/showthread.php?t=1901173)

---

