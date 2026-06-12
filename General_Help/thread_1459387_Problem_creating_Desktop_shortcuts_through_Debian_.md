---
title: "Problem creating Desktop shortcuts through Debian dpkg installer scripts"
date: 2010-04-21
forum: General Help
---

### Post by royalibrahim on 2010-04-21
Hi,

I am creating a debian package (*.deb) for my application using the  command > **fakeroot dpkg-deb --build**  <mypackage>I am using debian pre/post installer scripts to  do certain tasks before/after installation/uninstallation. One such  task is to create a shortcut on the user's desktop to launch my  application. I am trying to do this by copying the *.desktop file from  /usr/share/applications/<mypackage>.desktop to "${HOME}"/Desktop.  As we are running the dpkg install command (or gdebi-gtk UI installer)  as root (sudo) unfortunately the process does not predicate the user on  whom behalf the install command is running. Hence the copy is not taking  place as expected. The script could not figure out the correct user if I  issue the command "logname" "id -un" "whoami" or "$USER" as all these  commands return the user as root. I also tried to create a symbolic link  on the users Desktop directory and failed to do that. 

Please help me how to solve this problem?

Also, I am using delivering a notification through a pop-up screen if  the user tries to remove/uninstall on his system that installed package  when one of the instance is running. This I am doing using "**notify-send**"  command of "**libnotify-bin**" package. To get the pop up screen I  need to run the command as 
> gksudo -u <user> "sudo dpkg --purge  <mypackage>"What my question is, since we are running this  using gksudo, why I need to give sudo command once again and why I am  getting "dpkg: requested operation requires superuser privilege" error  if I am not giving that?

---

