---
title: "Getting Grub to Update the Menu List?"
date: 2011-07-12
forum: General Help
---

### Post by TurtleKing on 2011-07-12
Currently, Grub list Ubuntu 11.04 and window 7. However, I installed Kubuntu in Ubuntu's place about 1 month ago. I tried sudo apt-get upgrade Grub, but that didn't fix it. Is there a way to tell grub to look for the actual Operating Systems installed on the computer?

---

### Post by hhh on 2011-07-12
> **TurtleKing said:**
> I tried sudo apt-get upgrade Grub, but that didn't fix it.
It's sudo update-grub .

---

### Post by Elfy on 2011-07-12
I run Xubuntu. It ran the grub config. It calls itself 

'Ubuntu, with Linux 2.6.38-8-generic'

I think it's likely that any *buntu will be called Ubuntu by grub. I could be wrong though ;)

If that is the case, have a look here for title tweaking - [http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by TurtleKing on 2011-07-16
> **hhh said:**
> It's sudo update-grub .
Tried this and still list Ubuntu.

> I think it's likely that any *buntu will be called Ubuntu by grub.
Is this the case with other folks? I think it listed Kubuntu the first time I got it (was 4 months ago).

If so, then I rather leave it alone and not configure it to read Kubuntu.

If not, then I definitely want to fix and possible find out what was wrong.

---

