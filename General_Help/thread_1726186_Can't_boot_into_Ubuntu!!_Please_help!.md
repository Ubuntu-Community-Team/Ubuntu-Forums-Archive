---
title: "Can't boot into Ubuntu!! Please help!"
date: 2011-04-10
forum: General Help
---

### Post by metrogdor22 on 2011-04-10
I am currently running Xubuntu on a flashdrive. However, I just bought a 1TB hard drive, which I partitioned in half to use for Ubuntu. I successfully installed Ubuntu from a CD I burned with Xfburn. Whenever I try to boot to the Ubuntu partition, I get to the GRUB menu(Run Ubuntu, Run Ubuntu Recovery Mode, etc.). I choose Run Ubuntu, then my screen goes blank. I hear 2 quick drum beats, and then my monitor goes into standby - indicating that it's not doing anything. Why can't I boot into Ubuntu?

---

### Post by Dutch70 on 2011-04-10
Thats kind of odd. 
Did you try to run Xubuntu or Ubuntu (whichever it is) from the live cd to make sure it worked well with your hardware?

The easiest thing to try first would be nomodeset.
[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1613132[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1613132")

---

### Post by metrogdor22 on 2011-04-10
> **Dutch70 said:**
> Thats kind of odd. 
Did you try to run Xubuntu or Ubuntu (whichever it is) from the live cd to make sure it worked well with your hardware?

The easiest thing to try first would be nomodeset.
[[COLOR=Red]http://ubuntuforums.org/showthread.php?t=1613132[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1613132")

I don't have any problems running persistent Xubuntu if I run it with nomodeset(I know how to do that, as I use Xubuntu as my primary OS).

---

### Post by lmarmisa on 2011-04-10
You should reinstall GRUB2 following the procedure METHOD 3 - CHROOT of this link:

[https://help.ubuntu.com/community/Grub2#METHOD 3 - CHROOT]("https://help.ubuntu.com/community/Grub2#METHOD 3 - CHROOT")

---

### Post by Quackers on 2011-04-10
If you have to use the nomodeset option to boot a live desktop you will need to use it the first time you boot Ubuntu (until graphics drivers are installed).
When booting from the hard drive hold down the shift key.
This should bring up the grub menu which will have your Ubuntu entry highlighted at the top of the menu. 
On this screen press the "e" key
On the next screen, using the arrow keys, navigate to the end of the kernel line which currently ends "quiet splash" (without quotes).
After quiet splash press the space bar to leave a space then type in nomodeset then press ctrl + X to boot.

---

