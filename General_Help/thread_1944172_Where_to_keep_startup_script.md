---
title: "Where to keep startup script?"
date: 2012-03-20
forum: General Help
---

### Post by rng on 2012-03-20
I have a script which I want to start as the computer starts. Do I keep it in ~/.config/autostart/ or in /etc/xdg/autostart. Also do I need to make a .desktop file or I can simply place the script there? Also what if I want script to run with sudo command and to open a terminal and run in there. Thanks for your help.

---

### Post by llama320 on 2012-03-20
I can't answer all of that, but I think the easiest way to get a startup program running is to use the "startup applications" program -- I'm not sure what the cmd line name for it is, but if you type the above into the search bar it should pop up. The program will generate a .desktop file for you.

I'm not totally sure what to do to get root privileges, but my guess is putting the .desktop file that Startup Applications generated into /etc/xdg/autostart would be a good first step.

If you want to check if the script is being run as root, you can use the command ```
whoami
``` which will come out as "root" if you've got the right privileges. You can output that to a file ```
whoami > ~/sanity_check 
```, use an if statement, etc

---

