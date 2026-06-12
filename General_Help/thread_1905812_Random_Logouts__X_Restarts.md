---
title: "Random Logouts / X Restarts"
date: 2012-01-07
forum: General Help
---

### Post by Henkdroid on 2012-01-07
HI all, my computer running  Oneiric seems to have a problem where I'll intermittently get logged out with a black screen with white writing (it flashes past too quickly to see). I think it may be linked to a line in /var/log/X.org.0.log, here is the line: > 
[   195.615] (II) XKB: reuse xkmfile /var/lib/xkb/server-89D0835B7D65837BCF1AA41FF54A5C5DF983ED35.xkm 
Does anyone know a solution?

---

### Post by bluexrider on 2012-01-07
It could be a hardware issue too. Does your PC run hot?

---

### Post by Henkdroid on 2012-01-07
Here is the output of sensors
> acpitz-virtual-0
Adapter: Virtual device
temp1:        +52.0°C  (crit = +127.0°C)
temp2:        +51.0°C  (crit = +100.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +51.0°C  (high = +100.0°C, crit = +100.0°C)
Core 1:       +51.0°C  (high = +100.0°C, crit = +100.0°C)

thinkpad-isa-0000
Adapter: ISA adapter
fan1:        3325 RPM
temp1:        +52.0°C  
temp2:        +47.0°C  
temp3:        +34.0°C  
temp4:            N/A  
temp5:        +37.0°C  
temp6:            N/A  
temp7:        +35.0°C  
temp8:            N/A  
temp9:        +44.0°C  
temp10:       +52.0°C  
temp11:       +41.0°C  
temp12:           N/A  
temp13:           N/A  
temp14:           N/A  
temp15:           N/A  
temp16:           N/A  

---

### Post by imachavel on 2012-01-07
looks fine:

[http://antville.org/static/www/mrtg/temperature1.html](http://antville.org/static/www/mrtg/temperature1.html)

checked everything else?

have you tried sudo apt-get update or
sudo apt-get upgrade to see if it will fix broken files? That is assuming you have broken files. Ehh.. idk, I'm curious myself though I'll try and watch this thread

---

### Post by Henkdroid on 2012-01-07
What would you recommend checking?

---

### Post by imachavel on 2012-01-07
look at this thread:

[http://ubuntuforums.org/showthread.php?t=1665405](http://ubuntuforums.org/showthread.php?t=1665405)

or maybe it's unity 2d but I don't think so:


[http://joeslifewithubuntu.blogspot.com/2011/10/ubuntu-1110-check-list-after-installing.html](http://joeslifewithubuntu.blogspot.com/2011/10/ubuntu-1110-check-list-after-installing.html)

let me look around a little more, could be a lot of things. Ok this is my read out:

apt-cache policy unity
unity:
  Installed: (none)
  Candidate: 3.8.16-0ubuntu1~natty3
  Version table:
     3.8.16-0ubuntu1~natty3 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty-updates/main i386 Packages
     3.8.10-0ubuntu2 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty/main i386 Packages

from this command

apt-cache policy unity

can you run that in terminal? I'm not sure what your policy should look like, but if you can give a read out of that, it may help the mods help you and I think they know much more about this OS then I do.
Just to be safe, please list anything you feel important, partition settings, bios settings, boot drive settings, configuration settings, recent changes to OS configuration, recent things installed.
now please also, run these:

sudo apt-get install update

and give a read out of your syntax. I'm not sure it will fix the problem, but let's just get that machine diagnosed until the mods come in with some better advice.

---

### Post by Henkdroid on 2012-01-07
Here's the two commands: 
>  apt-cache policy unity
unity:
  Installed: 4.24.0-0ubuntu2.1xorgedgers1
  Candidate: 4.24.0-0ubuntu2.1xorgedgers1
  Version table:
 *** 4.24.0-0ubuntu2.1xorgedgers1 0
        500 [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/) oneiric/main i386 Packages
        100 /var/lib/dpkg/status
     4.24.0-0ubuntu2.1 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-updates/main i386 Packages
     4.22.0-0ubuntu3 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric/main i386 Packages

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package update


---

### Post by bluexrider on 2012-01-07
check your /.xsession-errors file for a clue and also /var/log/ConsoleKit/history

---

### Post by Henkdroid on 2012-01-07
Here's my partition settings (it's in an album) [Here]("https://plus.google.com/u/0/photos/116897472948279469826/albums/5694290657382884465/5695046231263178450")

---

### Post by bluexrider on 2012-01-07
Sorry, I don't do google+ and what does the partitions have to do with the issue at hand

---

### Post by Henkdroid on 2012-01-07
Here's the /var/log/ConsoleKit/history: [Here]("https://docs.google.com/document/d/12m904_sMgelWOKVzVPPSpNu6zcKyD5SiXYVd4ErXoOc/edit")
(It's a link because it is too big and I don't know what to look for)

---

### Post by Henkdroid on 2012-01-07
imachavel asked me to put down partition info and here is a proper link [here]("https://plus.google.com/photos/116897472948279469826/albums/5694290657382884465?authkey=CI_Hv8jo5f3cyAE")

---

### Post by bluexrider on 2012-01-07
> **Henkdroid said:**
> imachavel asked me to put down partition info and here is a proper link [here]("https://plus.google.com/photos/116897472948279469826/albums/5694290657382884465?authkey=CI_Hv8jo5f3cyAE")

OK he must be looking at a different angle

---

