---
title: "Help editing xorg.conf"
date: 2006-02-04
forum: General Help
---

### Post by mc4 on 2006-02-04
Let me preface this by saying I am a total n00b at Linux.  I would like to learn, but every time I try there is always something that gets in the way of having a working installation. 

On my L2000 the acceleration setting on my video card causes X server not to start.  I need to add the line "noaccel" to the driver section of my xorg.conf file.  Ok that I get.  

However when I try to edit this file in standard mode or recovery mode I have the same problem.  I type "sudo nano /etc/x11/xorg.conf" and there's nothing there.  It treats it like I am creating a new file.  When I try to navigate to the dir using the command cd etc nothing happens.  When I type vdir I see no dirs.  I can look at the files in partian magic on my install of XP and the file is there.  Obviouisly I can't edit it though.  

I really want this to work but I'm this close to just going back to my exclusive XP install.

---

### Post by zodder on 2006-02-04
I believe the directory is "/etc/X11". (those are ones). I'm a n00b, so this is my first attempt to help. lol hope it works :)

---

### Post by MartinG on 2006-02-04
[QUOTE=mc4]Let me preface this by saying I am a total n00b at Linux.  I would like to learn, but every time I try there is always something that gets in the way of having a working installation. 

On my L2000 the acceleration setting on my video card causes X server not to start.  I need to add the line "noaccel" to the driver section of my xorg.conf file.  Ok that I get.  

However when I try to edit this file in standard mode or recovery mode I have the same problem.  I type "sudo nano /etc/x11/xorg.conf" and there's nothing there.  It treats it like I am creating a new file.  When I try to navigate to the dir using the command cd etc nothing happens.  When I type vdir I see no dirs.  I can look at the files in partian magic on my install of XP and the file is there.  Obviouisly I can't edit it though.  

I really want this to work but I'm this close to just going back to my exclusive XP install.[/QUOTE]If you've reproduced what you typed accurately, you've been bitten by the fact that Linux is case sensitive.  It's in /etc/X11, not /etc/x11

---

