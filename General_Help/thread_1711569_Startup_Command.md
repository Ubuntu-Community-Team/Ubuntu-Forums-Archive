---
title: "Startup Command"
date: 2011-03-21
forum: General Help
---

### Post by Julian Luna on 2011-03-21
Hello since I have to run a terminal command everytime I started up my computer and want my last ALSA Gnome Mixer settings to load; and I want them to load everytime I start up my pc; I need a command which does the next:

1.- Open a terminal
2.- Write "sudo alsactl restore"
3.- Run it
4.- Write "exit"
5.- Run it

Also I would like the same command to automatically mount my "Misc" (ntfs format) Partition everytime I start up. Because if I run Rythmbox without "Misc" mounted; my songs show up as missing files.

The problem is that it's not conforting to start up, open misc, close it, open rythmbox, open gnome alsa mixer, open terminal, search for the command (or learn it), run it, close terminal, play, etc, thx

---

### Post by Thund3rstruck on 2011-03-21
just put the command to run into ~/.bash_login or ~/.profile

---

### Post by veggen on 2011-03-21
> **Thund3rstruck said:**
> just put the command to run into ~/.bash_login or ~/.profile
Hmmm, if he does that, he'll be prompted for password every time (since commands require sudo), right? I don't think that's what he wants...

Try appending the commands to /etc/rc.local, without sudo.
For permanent mounting of your NTFS partitions, you may want to install NTFS Configuration Tool from the repo.

---

### Post by Julian Luna on 2011-03-22
Thanks bro the NTFS tool fixed that, now I want the ALSA gnome mixer to always start up as when I write sudo alsactl restore

---

### Post by Krytarik on 2011-03-22
> **Julian Luna said:**
> now I want the ALSA gnome mixer to always start up as when I write sudo alsactl restore
Then simply put it into "/etc/rc.local", like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

/sbin/alsactl restore

exit 0
```
Greetings.

---

### Post by Julian Luna on 2011-03-23
That sounds sweet but I don't seem to be able to write on it :(
The account i'm using on this ubuntu is the only account so I think it's like administrator...
Idk... how to write it? D:
Ty

---

### Post by jocko on 2011-03-23
Of course you have to edit it as root, not as a normal user. So open it with:
```
gksudo gedit /etc/rc.local
```

---

### Post by Julian Luna on 2011-03-23
Holly molly you are so wise guys. THANKS

---

