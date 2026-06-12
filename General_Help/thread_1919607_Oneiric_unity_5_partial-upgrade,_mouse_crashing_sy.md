---
title: "Oneiric unity 5 partial-upgrade, mouse crashing system"
date: 2012-02-03
forum: General Help
---

### Post by b8e5n on 2012-02-03
Hello every one,

I have a huge problem since this morning... I checked my updates as usual :), and it proposed me a partial-upgrade. During the process, i noticed that it was upgrading installing unity 5. The process finished without any problem, so I decided to restart the system to be able to enjoy it immediately!
After the reboot, the login menu appears, I log on myself and suddenly it went back to the login menu... after retrying several times, it was crashing the graphical interface showing me the terminal (apache started, blablabla, cron closed... weird fir cron...) forcing me to restart.
Then I discovered that it was cause by a movement of the mouse, as soon as i touche the mouse, it does what I said previously.
So I tried the classical "dpkg --configure -a" redo updates, and even restore broken packages under the debug menu (from the grub menu) which detected a partial-upgrade and propose me to finish it. It does the job (no errors), but nothing changes, and if I keep to restore the broken packages, it still asking for finishing the partial-upgrade.

Does anyone can help me? This is my working computer...
(I am not using the mouse at all, but this is some kind of limiting me...)

I went back to the debug menu, and when I do the repair broken packages it says :
.."no upgrades available...
The currently installed packages will be removed
Do you want to install the partial-upgrade (yN)"  --> I say yes
so it starts something (checking packages...)
Then it finish successfully and ask me to type "ENTER" to return to the menu. If I redo it, it will propose and do the same things...

---

### Post by goofey24 on 2012-02-03
Never, never accept a 'partial upgrade' as you can be sure it's going to 'bork' your machine.
Sorry I can not help with your problem.
Good luck :)

---

### Post by jerrrys on 2012-02-03
Partial upgrades

[http://ubuntuforums.org/showthread.php?t=1641400](http://ubuntuforums.org/showthread.php?t=1641400)

---

### Post by b8e5n on 2012-02-03
Thank you for this information. I did not know what was the cause of the "partial-upgrade" proposition...
Anyway, I am now sure that this was caused because I added the ppa of the daily build of unity-2d (I know daily build is not a good idea to use on work's computer :/).
What are my best options, between waiting (hopefully this is the weekend...) for new updates, or rollback to a more stable version, or update unity/unity-2d to a newer/working version and stick to it?
I haven't been able to find something really working to rollback in this case.

---

### Post by Frogs Hair on 2012-02-03
Be patient , it usually doesn't take long for withheld packages to get released or broken packages to be fixed if the PPA is well maintained. Run check for updates in the update manager from time to time .

---

### Post by b8e5n on 2012-02-03
Fine, thanks, I think I will just go home, that would be the best thing of the day I did ;)
Then I will just stick to the working version (if it does o_O).

PS: I tried to reinstall the removed packages from the partial-upgrade (gambas2) but it did not change anything. So probably a versions-compatibility (missing dep...)

---

### Post by jerrrys on 2012-02-03
A handy tool for PPA's:

ppa-purge

This program disables a PPA from your Software Sources and reverts your
system back to the official Ubuntu packages. You can use this to return your
system to normal after testing a new version from a PPA.

Its in the software center.

---

### Post by goofey24 on 2012-02-04
> **jerrrys said:**
> A handy tool for PPA's:

ppa-purge

This program disables a PPA from your Software Sources and reverts your
system back to the official Ubuntu packages. You can use this to return your
system to normal after testing a new version from a PPA.

Its in the software center.

Thanks for the helpful 'handy tool'.:)

---

### Post by b8e5n on 2012-02-06
Thanks for you help, I tried friday to "purge-ppa", but that did not changed anything...
Anyways, I found the problem in this [topic]("http://askubuntu.com/questions/101308/xorg-segmentation-fault-seems-to-be-relevant-to-evdev"), saying it was from xserver-xorg-core version2:1.10.4-1ubuntu4.2newyork1

To fix this, the solution is to downgrade it by this command:
```
sudo aptitude install xserver-xorg-core=2:1.10.4-1ubuntu4
```

---

### Post by jerrrys on 2012-02-06
Congratulations

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

