---
title: "Random Freeze and Resolution Problem when Opening Game in Full Screen (Natty)"
date: 2011-06-07
forum: General Help
---

### Post by -Inoe- on 2011-06-07
Ubuntu 11.04 Natty Narwhal (clean install), happens in both Ubuntu (Unity) and Ubuntu Classic session.
Opening game in full screen sometimes makes the system freeze (in other words, it is sometimes successfully opened and playable).
The music of the game still runs, but the screen hangs.
I am still able to exit the game through Esc key or other keyboard action depending on the game, but after the game exits and the screen **looks** normal, the system is still unusable. I can move the cursor, but clicking anything doesn't have any effects.
It happens too when switching from windowed to full screen mode.

**Another problem:** The full screen games open in an unmatched ratio to my screen resolution (1280x800), leaving the black area on the left and right sides.

Game tested:
- Frozen Bubble
- Powermanga
- Njam

Specs:
- Intel Celeron CPU 550 @ 2.00GHz
- 1GB of RAM
- Mobile GM965/GL960 Integrated Graphics Controller

Updated the graphic drivers from **ppa:xorg-edgers/ppa** and the kernel to 2.6.39 from **ppa:kernel-ppa/ppa** but it still happens.

Anyone experiencing the same problem? Are there any solutions?
Thanks in advance.

---

### Post by -Inoe- on 2011-06-09
NEW:

I found that the problem most likely has some relation to the kernel. I tried to install some other kernel versions (taken from Lucid and Maverick's repository), and found that the kernels 2.6.35 and above serves the similar problem with Natty's default kernel (2.6.38) and 2.6.39 from kernel-ppa.

The kernels I tested:
2.6.32-30 (Lucid)
2.6.32-32 (Lucid)
2.6.35-25 (Lucid)
2.6.35-28 (Maverick)

2.6.32-20 and 2.6.32-22 works well as I experienced in Lucid, but it brings the same problem I posted in other thread ([http://ubuntuforums.org/showthread.php?p=10671353](http://ubuntuforums.org/showthread.php?p=10671353)) that I experienced in Lucid: opening a full screen game while playing music makes the music lags for a moment.
I don't face this music lag problem with Natty's kernel, but having system freezes for the game is of course a more serious problem.

I have reported a bug to launchpad regarding the kernel ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/794992](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/794992)). Still, any help on this problem is greatly appreciated.

Note:
Foobillard (3D billiards game written using OpenGL) runs well. I don't know what is the difference of Foobillard to other games.

---

