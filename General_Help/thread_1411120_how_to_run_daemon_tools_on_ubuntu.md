---
title: "how to run daemon tools on ubuntu?"
date: 2010-02-19
forum: General Help
---

### Post by diopsi on 2010-02-19
im new to linux but it said "daemon tools installed" so i think they are installed, but i cant find em anywhere in program center :/ im using newest version of ubuntu

---

### Post by akakingess on 2010-02-19
> **diopsi said:**
> im new to linux but it said "daemon tools installed" so i think they are installed, but i cant find em anywhere in program center :/ im using newest version of ubuntu

Not quite sure what you are asking, but to see which daemons are running, you could install either "top" or "htop" , htop is just a colorful version of top, but both would be similar in some instances to "task manager" in Windows and should show you apps and daemons that are currently running. Hope this helps a little.  By the way, both top and htop are available within the Synaptic Package Manager or Ubuntu Software Center, whichever you choose to use.  Good Luck.

---

### Post by Dies on 2010-02-19
> **diopsi said:**
> im new to linux but it said "daemon tools installed" so i think they are installed, but i cant find em anywhere in program center :/ im using newest version of ubuntu

When you see "daemon" on a Linux system it has nothing to do with "Daemon Tools". You don't need any special "tools" to mount iso files on a Linux system
```

mount -o loop <pathtoiso> <somedirectory>
```
is all it takes.

It would be much better if you told us what exactly it is you're trying do, especially as you seem to be under the impression that Linux systems work just like Windows. ;)

---

### Post by akakingess on 2010-02-19
> **Dies said:**
> When you see "daemon" on a Linux system it has nothing to do with "Daemon Tools". You don't need any special "tools" to mount iso files on a Linux system
```

mount -o loop <pathtoiso> <somedirectory>
```is all it takes.

It would be much better if you told us what exactly it is you're trying do, especially as you seem to be under the impression that Linux systems work just like Windows. ;)

Oops, I guess I missed the point on that one completely, huh? ;)

---

### Post by diopsi on 2010-02-19
> **Dies said:**
> When you see "daemon" on a Linux system it has nothing to do with "Daemon Tools". You don't need any special "tools" to mount iso files on a Linux system
```

mount -o loop <pathtoiso> <somedirectory>
```
is all it takes.
 
It would be much better if you told us what exactly it is you're trying do, especially as you seem to be under the impression that Linux systems work just like Windows. ;)
im trying to run diablo 2 lod with wine, but its asking for cd, so i n to mount that .ccd file, like i do i windows. i alread tried mount it with some scripts but i think diablo is prodected witsafedisc or smth, i need daemon tools

---

### Post by doas777 on 2010-02-19
you have hit on the one usecase underwhich mount -o -loop is inadaqute. it mounts the content, but the system just doesn't treat it as an optical disk drive. never been sure why.

with some games, you can tell wine to mount the iso as the wine cdrom, but I've not had a lot of luck with that. it is usually recomended that you find a no-cd edition of the game (or take care of it yourself somehow [without breaking the law of course]).

drm is one of the major reasons that games fail in wine. you may have to find a way to remove it from the image (assuming that that is legal whereever you are).

---

### Post by Dies on 2010-02-19
> **diopsi said:**
> im trying to run diablo 2 lod with wine, but its asking for cd, so i n to mount that .ccd file, like i do i windows. i alread tried mount it with some scripts but i think diablo is prodected witsafedisc or smth, i need daemon tools


See this thread just in case it helps

[http://ubuntuforums.org/showthread.php?t=180124](http://ubuntuforums.org/showthread.php?t=180124)

---

### Post by skarychinezeguie on 2010-02-19
install daemon tools into wine?

---

