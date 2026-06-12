---
title: "web server program help"
date: 2010-04-11
forum: General Help
---

### Post by Deepfrost on 2010-04-11
Well I have installed Wine for the propose of running easyphp program which can be found at [www.easyphp.org](www.easyphp.org). I installed it on my windows machine and like it. I want to run it on this machine because I have it hooked up to my tv and I have a wireless mouse and keyboard so I can program or whatever from the bed. Anyways, I need to remove the stuff I installed though this tread. [http://ubuntuforums.org/showthread.php?t=1448625](http://ubuntuforums.org/showthread.php?t=1448625)  Not that I don't appreciate the help because I do. The reason for removing the installed stuff is because I believe it is occupying port 80 which I need open for easyphp. How do I uninstall  this stuff I installed?

---

### Post by Deepfrost on 2010-04-12
If anyone else runs into this problem this is how to fix.

[LIST]
[*]Open terminal
[*]type  sudo apt-get remove <program> the programs for me were apache2 php5 php5-mysql mysql-server
[*]When terminal asks you if you would like to continue type y
[*]Hit enter
[*]I suggest reading a few lines up in order to double check that it is removing the right program(s)
[/LIST]
Note: If there is are any icons left over the program sure be uninstalled it is just a cosmetic glitch per say. just remove the icons.
[CENTER]**Easy as that.**

[/CENTER]

---

