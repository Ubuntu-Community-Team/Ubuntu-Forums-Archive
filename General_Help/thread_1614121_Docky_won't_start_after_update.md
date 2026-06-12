---
title: "Docky won't start after update"
date: 2010-11-05
forum: General Help
---

### Post by wolf_3d on 2010-11-05
Hello,

In today's updates there was an update for Docky to go from 2.0.5 to 2.0.6. The thing I thought was odd was that the update was only around 600 or 700kb in size where as its normally around ~13mb.

When I restarted the computer docky loaded but the whole system froze and wouldn't respond to either mouse or keyboard so I did a hard restart. 

Now Docky won't load either on restart or from the program menu but it is present in the System Monitor (see attached image).

How do I get Docky back?

---

### Post by wolf_3d on 2010-11-06
Bump #1

---

### Post by searchfgold6789 on 2010-11-06
See if it runs from the terminal.
```
docky
```Or purge and reinstall it.
```
sudo apt-get purge docky
sudo apt-get autoremove
sudo apt-get install docky
```Or maybe the Docky package or one of its dependencies is broken. You can check using Synaptic.

---

### Post by wolf_3d on 2010-11-06
Hi,

This is the terminal output;

```
****@CUSTOM-MACHINE:~$ docky
[Info  13:44:27.699] Docky version: 2.0.6 Release
[Info  13:44:27.706] Kernel version: 2.6.32.25
[Info  13:44:27.707] CLR version: 2.0.50727.1433
[Error 13:44:28.063] Another Docky instance was detected - exiting.
```

I'll try the purge remove and reinstall now.

---

### Post by wolf_3d on 2010-11-06
OK,

I have followed those steps but the problem is remaining.

I started Docky through the terminal this time once it had installed and the attached screenshots is the result.

Something is seriously up with the 2.0.6 version.

---

### Post by wolf_3d on 2010-11-06
Hi all,

This issue is now appears to be fixed. My problem was similar to this guy; [http://ubuntuforums.org/showthread.php?t=1441185](http://ubuntuforums.org/showthread.php?t=1441185)

I did what the guy in post #6 did which was;
> I got the same errors as you.
This worked for me. Hope it helps

in terminal type

Quote:
killall docky
then in nautilus, or whichever filemanager you use, navigate to

/home/USER/.local/share

and delete the docky folder

restart docky.

I'm guessing some settings got messed up and deleting the docky folder resets to default versions.

Cheers
Rich

And now my Docky is back and working well as my terminal indicates;

```
****@CUSTOM-MACHINE:~$ docky
[Info  14:28:43.364] Docky version: 2.0.6 Release
[Info  14:28:43.370] Kernel version: 2.6.32.25
[Info  14:28:43.371] CLR version: 2.0.50727.1433
[Warn  14:28:45.896] [DockController] "BatteryMonitor" seems to have been abaondoned... disabling.
[Warn  14:28:45.901] [DockController] "Bookmark Items" seems to have been abaondoned... disabling.
[Warn  14:28:45.902] [DockController] "Clock" seems to have been abaondoned... disabling.
[Warn  14:28:45.902] [DockController] "Mount" seems to have been abaondoned... disabling.
[Warn  14:28:45.905] [DockController] "NPR" seems to have been abaondoned... disabling.
[Warn  14:28:45.906] [DockController] "Recent Documents" seems to have been abaondoned... disabling.

```

searchfgold6789 thanks for the post I'll mark this as solved soon.

---

