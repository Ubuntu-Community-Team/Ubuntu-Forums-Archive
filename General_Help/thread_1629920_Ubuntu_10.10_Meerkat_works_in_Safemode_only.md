---
title: "Ubuntu 10.10 Meerkat works in Safemode only"
date: 2010-11-24
forum: General Help
---

### Post by OldTech57 on 2010-11-24
Please forgive me if this issue is addressed elsewhere as this is my first experience with Ubuntu. I loaded the operating software on a new drive and all seemed to load ok. When I go to log in to ubuntu I get the window with my user name and a request for password. I type my password and go forward and the ubuntu appears to go into the program then the login window comes back on the screen. It almost seems like it is stuck in a loop???...If I put in my password and choose safemode I can access the operating system. I have next to no experience with the linux platforms so any help in this would be greatly appreciated. Thank-you in advance ...Bill

---

### Post by rob1408 on 2010-11-30
As your post is five days old you may have fixed it, if so I apologise.  I had the same symptoms as you after an install of Linux Mint 10 and the following worked for me (Mint is built on Ubuntu).

1)Hold down the 'shift' button during boot so that the grub menu appears.
2)Select 'recovery mode' 
3)Wait for all the on-screen text to finish and then select the 'net root' option (towards the bottom)
4)You should eventually arrive at a prompt for your password, enter it.
5)Type the following command: 

sudo nano /etc/X11/xorg.conf    (be sure to make the 'X' in X11 a capital)

6)Enter the following :

Section "ServerFlags"
Option "AIGLX" "off"
EndSection

(exactly the same as above)

7) Press 'Ctrl' and 'o' followed by 'enter'
8) Press 'Ctrl and 'x'
9) Type 'sudo reboot now'

After the reboot I was able to log in to Mint using standard Gnome rather than the failsafe option.

---

### Post by aloneshadow207 on 2010-12-21
The same thing happen to me although I thought it was because of my machine being to old. Now I realized that there could be something wrong with the installation. I tried what the guy suggested but no luck. Still stuck in the purple screen. If someone could help... Thanks in advance

---

### Post by Dream Theather on 2011-02-22
I have the same problem here, whenever I log in using my username / password, its just loops and keep asking my password but when i choose safemode I am able to log in. Hoping for someone's help. Is this a hardware or installation issue?

---

### Post by listoff on 2011-03-09
I'm a new guy at this too and had the same problem.  I did the fix above and it worked like a charm!  Thanks for the help!!!  I have no clue what-so-ever what that code did, but it did work for me.

---

### Post by SR_ELPIRATA on 2011-06-24
Thanks rob, it worked like a charm for me, old Compaq Deskpro EN (P3 733 512mb 1mb video card)

:)

---

