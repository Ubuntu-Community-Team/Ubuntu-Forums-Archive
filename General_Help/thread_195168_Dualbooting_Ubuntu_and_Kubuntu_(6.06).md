---
title: "Dualbooting Ubuntu and Kubuntu (6.06)"
date: 2006-06-12
forum: General Help
---

### Post by jw29 on 2006-06-12
Hello,

I was wondering if somebody could tell me or point me in the right direction for dualbooting to have both Ubuntu and Kubuntu 6.06 so I could switch back and forth between them.

Thanks.

---

### Post by aysiu on 2006-06-12
You don't need to dual-boot them.

You can have both installed on one partition and choose at the login screen which one you want.

Just install Ubuntu and then follow these instructions:
[http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html)

---

### Post by Ramses de Norre on 2006-06-12
No dualbooting required =) Just do ```
sudo aptitude install ubuntu-desktop kubuntu-desktop
``` and you'll be asked to use gdm or kdm, with gdm you can shut down right away from gnome, with kdm you'll need to log out gnome and shutdown from kdm, and it's the other way around from kde. Choose the one you'll use the most, you can change it afterwards.

To change the splash if that's changed and you liked the other more do sudo update-alternatives --config usplash-artwork.so and pick your choice.

You can choose which one to start on login screen in the sessions menu.

---

### Post by glotz on 2006-06-12
Some people actually *prefer to* double boot them. Please include instructions for doing that as the original poster might be looking for it specifically.

---

### Post by aysiu on 2006-06-12
It's true. Not too long ago, I dual-booted them because I liked my installations clean.

If you want to dual-boot them, install Ubuntu and choose to erase the entire disk.

Then install Kubuntu and choose to resize the partition and use the free space.

Ta-da!

---

### Post by jw29 on 2006-06-12
Well, either way it doesn't matter.  I'm currently running Ubuntu 6.06 and I don't have many files on it, so I can back everything up on a flash drive and just experiment with it.  I was just a bit unsure how to get started, as I've never dualbooted two OS's/distributions before.

Thanks for your help with both methods of doing it.

---

### Post by ajgreeny on 2006-06-12
If you install kubuntu-desktop on ubuntu, or ubuntu-desktop on kubuntu and have enough disk room for both desktop environments, you can actually have both desktops running at the same time by going to "switch user / Start new session".  This will allow you to keep the session you are using open (this will be on Ctrl+Alt+F7) and start an extra one (this will be on Ctrl+Alt+F8).  You can then swap between them using Ctrl+Alt+F(x) and see which is best for you.

Wonderful Linux/Ubuntu.  Try doing that in Windows.

---

### Post by Slim Odds on 2006-06-12
[quote=ajgreeny]Wonderful Linux/Ubuntu.  Try doing that in Windows.[/quote] 
How do I try that exactly? LOL :p

---

### Post by ajgreeny on 2006-06-13
Precisely!!  You can't do it in windows, along with all sorts of other things that we can.

---

