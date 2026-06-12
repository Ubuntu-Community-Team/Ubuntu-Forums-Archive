---
title: "Can't load Ubuntu"
date: 2011-07-05
forum: General Help
---

### Post by Pirate Zoro on 2011-07-05
First, let me start off by saying that for the past 5-6 months I've been using Linux stand-alone without Windows at all. Recently though, I got netflix and found that there is no support for Linux distros. So, begrudgingly, I installed a small Windows Partition on my computer. So here's the problem: I can't boot back into Ubuntu. Whenever I turn on my computer, it automatically boots up into Windows 7. I know my Ubuntu partition is still there, because when I boot from my live disc I can see it. Is there a way I can fix this using Windows and/or a live disc?

---

### Post by samigina on 2011-07-05
Boot your computer from the Ubuntu Live CD, in the live session open a terminal window and type:

sudo update-grub2

---

### Post by seawolf167 on 2011-07-05
This is because Windows installed it's own MBR overwriting GRUB2. You'll want to reinstall GRUB2 following the instructions [here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2").

---

### Post by samigina on 2011-07-05
Another [how-to]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by Pirate Zoro on 2011-07-05
Thanks guys, worked like a charm :KS

---

### Post by seawolf167 on 2011-07-05
Glad it is working now!

---

