---
title: "Howto time a script?"
date: 2010-11-26
forum: General Help
---

### Post by krelverehan on 2010-11-26
Hey everyone,

I made up this script for whenever I do a fresh install of ubuntu:

```
#! /bin/bash

sudo apt-get -y update
sudo apt-get -y remove gnome-bluetooth empathy evolution evolution-webcal gwibber totem gnome-mag rhythmbox transmission-gtk onboard evolution-indicator gwibber-service evolution-common evolution-data-server empathy-common nautilus-sendto-empathy totem-common
sudo apt-get -y install quodlibet qbittorrent htop vlc gparted
sudo apt-get -y autoclean
sudo apt-get -y autoremove
sudo apt-get -y upgrade
```

I was wondering if there was a timer that would print out the time elapsed for the script to run its course.

I have reason to believe that [FONT="Courier New"]**[COLOR="Red"]time[/COLOR]**[/FONT] command would be the right command, but I am unclear on how to use it (coding isn't my forte).

Thanks!
KV

---

### Post by Ocxic on 2010-11-26
time ./name_of_script

---

### Post by krelverehan on 2010-11-26
I get:

```
krel@namcle:~/Desktop$ time -f E -o /home/krel/Desktop/startup 
-f: command not found

real    0m0.151s
user    0m0.116s
sys     0m0.028s

```

But if I lose the '-f E -o' it prints out ```
real    0m2.819s
user    0m1.728s
sys     0m0.116s
```

---

### Post by DaithiF on 2010-11-27
where are you getting those parameters?  time doesn't take any parameters, just the command whose execution you want to time.

---

### Post by Ocxic on 2010-11-27
ya, just use "time ./script.sh"

the "real" time is the time you want to look at.

I got the parameters for the time man page, but it didn't work for some reason.

---

