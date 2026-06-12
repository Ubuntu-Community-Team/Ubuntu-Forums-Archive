---
title: "Wubi"
date: 2011-07-18
forum: General Help
---

### Post by ardit ,A, on 2011-07-18
I installed ubuntu today in XP with WUBI and then ubuntu installed bla  bla bla... but now not starting when PC boots then showing as usually XP  and Ubuntu tu choose. I choose Ubuntu and then shows something  "Microsoft Windows XP dev/sda1", which I dont remember all, then I go  there, then shows "error: unknown command 'drivemap'" but fastly hide these words and back me again at OS choose.


dont know where is problem :sad:

---

### Post by Frogs Hair on 2011-07-18
Check at the link. [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by bcbc on 2011-07-18
> **ardit ,A, said:**
> I installed ubuntu today in XP with WUBI and then ubuntu installed bla  bla bla... but now not starting when PC boots then showing as usually XP  and Ubuntu tu choose. I choose Ubuntu and then shows something  "Microsoft Windows XP dev/sda1", which I dont remember all, then I go  there, then shows "error: unknown command 'drivemap'" but fastly hide these words and back me again at OS choose.


dont know where is problem :sad:

This can be caused by pressing SKIP during the installation. It prevents an essential part of Wubi installs from being setup.

---

### Post by ardit ,A, on 2011-07-19
> **bcbc said:**
> This can be caused by pressing SKIP during the installation. It prevents an essential part of Wubi installs from being setup.

ohh maybe, cause when SKIP button showed at installation window I pressed it at every time showed :(

now I uninstalled ubuntu[with wubi], do I need to install and not pressing SKIP anymore ? :P

---

### Post by bcbc on 2011-07-19
> **ardit ,A, said:**
> ohh maybe, cause when SKIP button showed at installation window I pressed it at every time showed :(

now I uninstalled ubuntu[with wubi], do I need to install and not pressing SKIP anymore ? :P

Yes... that's right.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/620028](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/620028)

---

### Post by ardit ,A, on 2011-07-19
> **bcbc said:**
> Yes... that's right.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/620028](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/620028)

thankssssss very much :D now Ill try this, and I think its going to work fine :guitar:

---

### Post by ardit ,A, on 2011-07-19
[B]and 1 more question!


HOW MUCH DO I NEED TO WAIT TO COMPETE THIS MESSAGE AT WUBI

[/B][LEFT]******_***Downloading ubuntu-10.04.2-desktop-amd64***_*_**.iso.torrent**_*
[/LEFT]

---

### Post by bcbc on 2011-07-19
You can download it yourself and then you can reuse it e.g. burn to cd etc.

Once you've completed the download - before you reboot - look for it in C:\ubuntu\install\...installation.iso (or something.iso) and copy it out so that you have a copy. If you run wubi.exe and the .iso file is in the same folder it will use it instead of downloading a new one.

PS *copy* it, don't move it out of that directory or the ubuntu install (when you reboot) will fail.

---

