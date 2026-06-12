---
title: "unable to log on"
date: 2011-04-22
forum: General Help
---

### Post by chrisw71 on 2011-04-22
Hello everyone, running Xubuntu 10.04 here.  After installing and removing some packages in package manager I'm finding after reboot I cannot logon to the computer.  When the correct password is entered the screen goes to black briefly then returns to the logon screen.  It appears I can only logon to an xterm session.  Can anyone provide suggestion on how to proceed next?

Thanks,
Chris

---

### Post by Mario ROGER on 2011-04-22
Hello Chris

I don't use Xubuntu but I had some similar behavior on one Ubuntu laptop
I don't know why the user environment was broken

The solution found was :
[LIST=1]
[*]login in terminal mode on user account
[*]cd $HOME
[*]rename of .gnome2 (gnome2.sav) and .gconfd (gconfd.sav) directories 
[*]sudo shutdown now
[*]Start the computer
[/LIST]

After these actions the user was able to login in graphical mode. He lost some configurations but no blocking issue

NB : I don't know which dot directories are used by XFCE. May be you can know last updated files and directories by using "ls -lart" 

Hope this help to find a solution

Bye : Mario

---

