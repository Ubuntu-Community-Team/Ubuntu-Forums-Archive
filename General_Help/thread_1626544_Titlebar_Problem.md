---
title: "Titlebar Problem"
date: 2010-11-20
forum: General Help
---

### Post by ajitdmonte on 2010-11-20
Hi,
I'm new to Ubuntu and I am sure no one else is experiencing the problem I have. I log onto Ubuntu Desktop Edition by default on my laptop with the netbook edtion. I've been experiencing this problem since my upgrade to 10.10 from 10.04. I've installed compiz and emerald. When I maximize any window the titlebar goes missing and is there on the window as long as its restored or unmaximized. I've also noticed that every thing I open from VLC player to the file manager tends to open maximized. I hope this is not a new feature of 10.10 and hope am not reposting an old error.

Note: I've tried using the commands metacity --replace and it doesn't work since the titlebar is already there but goes missing only when a windows is maximized. In the screen when I opened VLC it opened maximized by default, this was not the case in 10.04...

Thanks for any help at all, this is getting bugging. Btw its the same even if i turn off all visual effects.

---

### Post by sohlinux on 2010-11-20
compiz is a bit buggy, it happens a lot.  if you right on the desktop and choose change desktop background - click on themes then choose one of the themes it should fix. if it keeps recurring then you will have to uncheck some of the compiz options, best not to have too many compiz options running

---

### Post by ajitdmonte on 2010-11-21
Now i've uninstalled compiz and emerald altogether... So I am using the "metacity" windows manager i guess. But when I start up there is no window manager running by default and I have to run metacity --replace. But when I close the Terminal it asks me if I want to kill the process... So if I close the terminal I have no window manager... What do I do now? Is there a way to reinstall metacity with factory settings or something? I don't want to reinstall ubuntu. Btw the titlebar is still missing maximized and it's there when the window is restored.

Note:When I logged into the Desktop Edition Safe mode, there is no window manager working by default there too, but by running metacity --replace via terminal the title bar appears when maximized and restored. So now how do I get it to work on the normal desktop login and how do I get the window manager to start automatically.

---

### Post by ajitdmonte on 2010-11-22
Come on need some help here... :(

---

### Post by sohlinux on 2010-11-22
sudo dpkg-reconfigure gdm

---

### Post by ajitdmonte on 2010-11-22
Hey,
nothing happened when I entered the command. :(

---

### Post by sohlinux on 2010-11-22
follow this [http://pinoygeek.org/forum/index.php?topic=443.0](http://pinoygeek.org/forum/index.php?topic=443.0)

:p

---

### Post by ajitdmonte on 2010-11-22
Hey mate,
Thanks a lot... I found out that when compiz was intalled, it also installed this app "maximux" which hides the title bar to incerease screen space... So I've removed that and all is well. Now could you tell me how to start metacity automatically on start up cause I have no window manager starting automatically on startup or should I follow the previous link?

Thanks a lot for the quick replies.

---

### Post by sohlinux on 2010-11-22
go to System - Preferences - Startup Programs then click the Add button and type in Metacity as the Name and type /usr/bin/metacity as the command to run the application. done :)

---

### Post by ajitdmonte on 2010-11-22
Awesome!!!! Solved.
Thanks a lot sohlinux!!!

---

### Post by sohlinux on 2010-11-22
> **ajitdmonte said:**
> Awesome!!!! Solved.
Thanks a lot sohlinux!!!

:p

---

