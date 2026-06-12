---
title: "help uninstalling Veetle"
date: 2010-10-20
forum: General Help
---

### Post by jimstar79 on 2010-10-20
Hi all, 

Anyone know how to uninstall Veetle from Ubuntu 10.04?

A straight up Google search does not yield many results!

Thanks in advance.

PS: have already tried sudo apt-get remove veetle

PPS: was installed as a .sh file, if that helps.

Cheers

---

### Post by searchfgold6789 on 2010-10-20
Try running the .sh file again. It might detect your installation and ask you if you want to uninstall.

---

### Post by jimstar79 on 2010-10-20
will do...back soon

and thanks for the quick reply!

---

### Post by jimstar79 on 2010-10-20
nope, unfortunately it does not give option to uninstall, just ran a fresh installation :(

have located the file on my machine as .veetle_vlc

it comes with loads of lib files and they may be causing me the trouble.

hmmm?

---

### Post by sgage on 2010-10-20
You might have better luck on the Veetle Forums - they seem to have a Linux forum there.

[http://forums.veetle.com/forums/](http://forums.veetle.com/forums/)

---

### Post by jimstar79 on 2010-10-20
cheers, sgage, i already had a look there before I posted here. 

I managed to get rid of this problem, without uninstalling Veetle,  by doing this:

sudo chown <user>:<user> /home/<user>
sudo reboot 

where user is your username)

this prevented an ICEauthority problem from occurring and also seemed to resolve some Sound issues I was having.

Hope this helps somebody out there!!

PS: I had also previously uninstalled VLC

with: sudo apt-get remove vlc


PS: found that info over here: [http://www.linuxquestions.org/questions/linux-desktop-74/iceauthority-error-in-ubuntu-8-10-a-681312/](http://www.linuxquestions.org/questions/linux-desktop-74/iceauthority-error-in-ubuntu-8-10-a-681312/)

and here:

[http://ubuntuforums.org/showthread.php?t=1021106&page=2](http://ubuntuforums.org/showthread.php?t=1021106&page=2)

---

### Post by jimstar79 on 2010-10-20
how to give beans?

---

### Post by DeLaJamie on 2011-04-24
Thanks!  Stupid Veetle...but this solved my problem instead of uninstalling.  My sound was also screwed up.  Didnt think to just chown my entire home folder.  Last time i hastily try to stream a lakers game!

---

