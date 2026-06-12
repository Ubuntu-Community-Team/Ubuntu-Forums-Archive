---
title: "How to get x11 mouse pointers working?"
date: 2010-06-10
forum: General Help
---

### Post by rahilm on 2010-06-10
I've been facing this problem since months before I decided to find an answer. I downloaded a cursor theme from gnome-look.org and then installed it by dragging the tarball to the themes window. It said theme is installed. But the effects are not visible yet. I then shoot up firefox to see the new pointer working but not outside firefox.
I even noticed the new pointer theme works in nautilus for all except pointing (it works while resizing, selecting text, loading but not the regular pointing).

I searched the forums and found a similar problem:
[http://ubuntuforums.org/showthread.php?t=977004](http://ubuntuforums.org/showthread.php?t=977004)

the solution doesn't work because there is no "cursor theme" option in ccsm. i've attached a screenshot too.

Is it a bug? do i need to disable compiz to "have my own desktop"? Is there a solution?

---

### Post by tajunta on 2010-06-25
I have precisely the same problem. Different cursor actions work, but the regular pointer is not the theme pointer, but default pointer. I also don't have any mouse pointer settings in CCSM. 

Are we missing something obvious, or what's going on..? When disabling compiz the installed cursor themes work just fine. 

Edit: This worked for me: [http://ubuntuforums.org/showthread.php?t=1472439]("http://ubuntuforums.org/showthread.php?t=1472439")

---

### Post by rahilm on 2010-06-26
works great. . .thnx..
Still one app which is exceptional,
would you check if the pointer theme works on vlc??.. because it doesn't on mine..

---

### Post by vince2678 on 2010-08-20
Compiz cannot update the mouse cursor theme when it is updated in GNOME.    Install this package to allow compiz to notice the change and feel   free  to modify it however you want. PLEASE read he control info!

Unfortunately only works with GNOME. If anyone has LXDE and XFCE please    send me info on how it stores info about cursor theme and size and the    program used for changing cursor theme. I have KDE in a VM so I'll  try   something there.
 
 LINK: [_http://ubuntuforums.org/showthread.php?t=1557297_]("http://ubuntuforums.org/showthread.php?t=1557297")

READ CAREFULLY!

---

### Post by Vrroom on 2010-08-20
There is a simple solution.....
open nautilus with root access and go to /usr/share/icons
There is a "default" folder. Make a backup and delete all files from there.
Now copy all files from your favorite mouse theme folder and paste them into "default" folder.
Log out and come back.
No more pointer problems :)

---

### Post by r5r4y on 2011-01-21
You just need to change the default cursor folder which is DMZ-White in /usr/share/icons and put there your cursor theme, But make a backup first!!

---

