---
title: "Nvidia driver doesn't work"
date: 2010-10-21
forum: General Help
---

### Post by fiddler616 on 2010-10-21
Hello,

So I just installed Maverick on my HP tx1000. Jockey offered me two drivers for my NVidia Go 6150. I tried the recommended one--and it seemed to be working. It had a green light next to it in Jockey, Compiz worked, etc.

Then I rebooted.

Except it didn't reboot--the disk thrashed for a while, and then I was met with a black screen. I tried recovery mode and got a bash prompt...which crashed when I ran `startx'. Then I tried Failsafe X, which did work. After some experimentation, I realized it was the Nvidia driver at fault, so I tried the not-recommended one, which didn't work, and now I've disabled both of them. But isn't there a proper driver for me to use? IIRC, I was using a restricted one with Lucid, and it was working all right.

Fun fact: The day before I installed Maverick, Windows 7 randomly decided to not boot all the way. It would show the splash screen, and then hang with a black screen too. But it works in Safe Mode. And had been working fine for a while beforehand. There must be demons in my graphics card.


Thanks in advance.

---

### Post by pqwoerituytrueiwoq on 2010-10-21
get the one from nvidia
put the run file somewhere you can get to it (i use the /opt folder) you will needed it after kernal updates

once that is done
```
#close GUI
sudo service gdm stop
#press alt+F1
#login
sudo sh /opt/something.run
#go through the process
sudo service gdm start
```
i have been doing it like this since ubuntu 9.04

to uninstall i think you only have to recompile the kernel

---

### Post by fiddler616 on 2010-10-21
That did it, thanks a lot!



[SIZE="1"]Note for future Googlers: The site with all the drivers is right [here]("http://www.nvidia.com/object/unix.html").[/SIZE]

---

### Post by fiddler616 on 2010-10-22
I spoke too soon. That procedure worked as soon as I installed the driver and restarted the GDM, but I have the same problem upon rebooting.

--Posted from Failsafe X.

---

