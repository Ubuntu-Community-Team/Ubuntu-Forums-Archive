---
title: "Most objects in games I play under Wine are black"
date: 2011-07-04
forum: General Help
---

### Post by colobix on 2011-07-04
How do I fix this?
I use playonlinux to install the games, so I don't install them manually.
Also I think it might have something to do with the graphics settings I did when it told me to install a version of Wine to make the game work. I have no idea how many gigabyte or megabyte my graphics card is so I selected the highest number.
I don't know if that has something to do with anything though.

---

### Post by 3Miro on 2011-07-04
Wine programs are hit and miss. One game may run perfectly and another may fail altogether. The best place for wine help is the winehq forums, you can search for specific games with specific instructions.

For the graphics settings, you can try a number of things:

- make sure you have the latest available proprietary driver (from additional drivers).
- if you don't know how much video RAM you have, try something smaller than what you have now.
- try disabling compiz (appearance -> desktop effects -> none) or disable Unity ( logout -> Ubuntu Classic (No Effects) -> login).

---

### Post by colobix on 2011-07-04
Thanks a lot. But it didn't solve anything.
I do have the latest nvidia driver and killed compiz.
But all my games are still for the most part night.
When I play Sonic Fan Remix, I can only see the moving objects such as coins, sonic's legs and the sky. So that game is actually more challenging and fun to play with all the objects being black.
But games such as MW2, CoD, Portal and Sims 3 are unplayable.
However, I don't know where I can change the wine graphics memory settings now. It came up automatically the last time.
I check the wine configurations in the start menu but no luck there. Some graphics settings, but not that.

---

### Post by 3Miro on 2011-07-04
Which Nvidia card is this? Sims 3 should work well enough, it was reasonable when I tried it on GeForce 9300 with Ubuntu 8.10.

Winehq guys know more about wine than most people on this forum:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=16664](http://appdb.winehq.org/objectManager.php?sClass=version&iId=16664)

---

### Post by colobix on 2011-07-04
I don't know. Nvidia settings says the driver version is 270.41.06.
Where do I find the nvidia card version?

---

### Post by 3Miro on 2011-07-05
On the left of the Nvidia settings, do you have something like:
```
GPU 0 - (GeForce GTX 260)
```
yours would be different.

---

### Post by mikejonesey on 2011-07-05
hmmm there was an update to xorg about a year ago now that caused alot of black areas in wine apps... from memory there was a setting you could add to disable some xorg rendering setting...

update: had it in tomboy...
[HKEY_CURRENT_USER\Software\Wine\X11 Driver]
"ClientSideWithRender"="N"

---

### Post by colobix on 2011-07-05
Yea. Mine said 460M
Okay so where do I change these settings in wine?
Also, 460m doesn't sound that good. Is it good?

---

### Post by mikejonesey on 2011-07-05
the wine settings are edited through regedit;

cd .wine/drive_c/windows/
wine regedit.exe

or if you use pol (play on linux - i recommend for wine apps in linux...) there is a little button you can click...

---

### Post by 3Miro on 2011-07-05
> **colobix said:**
> Yea. Mine said 460M
Okay so where do I change these settings in wine?
Also, 460m doesn't sound that good. Is it good?

GTX 460 is fairly powerful, you should have no trouble with Sims 3 (don't know about other games as I have never played them).

Try what mikejonesey suggests.

---

### Post by colobix on 2011-07-05
okay I deleted the .playonlinux folder again, so now it asks me again how much memory my graphic board has.
460 isn't an alternative there. 512 is the closest number.
What should I do here?

---

### Post by 3Miro on 2011-07-07
460 is a model number and you probably have something in the range of 800MB - 1.2GB. 512 should be a good lower estimate.

---

