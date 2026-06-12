---
title: "how to give a user sudo privilege from command line?"
date: 2011-03-14
forum: General Help
---

### Post by georgelappies on 2011-03-14
Good day all, I have a bit of a problem. I adjusted some settings in the desktop settings folder in KDE. I had only one user account on the machine. Next time I rebooted I could not log into KDE (it kept bombing out). I had to log into the console. Finally I managed to create a new account with useradd but this user cannot sudo…

*

My problem is that my home directory is encrypted, so I need a new user with sudo privileges to delete all the kde files and folders in my original users home directory so that I can start with a new KDE setup (which won’t be a bad thing since I tinkered a lot).

*

How can I add sudo privileges to the new account (I presume I can do it by logging in with my sudo account in a terminal login?

*

Please kind ubuntu population assist me with getting my music, videos and docs back ;)

---

### Post by prshah on 2011-03-14
> **georgelappies said:**
> How can I add sudo privileges to the new account (I presume I can do it by logging in with my sudo account in a terminal login?

I cannot understand how giving a new username sudo privileges will help you, but you can do this by adding the newuser to the admin group```
sudo adduser newusername admin
```

If you do not have access to sudo at all, please reboot into the recovery console's root terminal.

---

### Post by georgelappies on 2011-03-14
Thanks, won't a sudo user have access to my old home directory even if I need to supply a password to open it. I wanted to delete all files and folders in my old home directory exept /music /data /videos /opt /Documents thus forcing Kde to create new config files ans folders and allowing me to log in and not crash when trying to login with saved incompatible settings?

Perhaps any other suggestions? I guess I can delete these via commandline but it will be much quicker via graphical interface (I am a noob wrt command line still ;))

---

### Post by highspider on 2011-03-14
see also

```

man sudoers 
```-and as root-
```
gedit /etc/sudoers

```search the web for /etc/sudoers to have more human reading info like
[http://www.ghacks.net/2010/01/06/how-to-add-users-to-etcsudoers/](http://www.ghacks.net/2010/01/06/how-to-add-users-to-etcsudoers/)
this gui is not ubuntu! but get u searching in right direction
but thats problem more then any ever uses :)

---

### Post by prshah on 2011-03-14
> **highspider said:**
> 
```
gedit /etc/sudoers

```

DON'T do this! It's an almost surefire way to break your sudo. This approach is not recommended:

a) It doesn't do anything to clear your problem
b) editing /etc/sudoers without using the "visudo" command is highly NOT recommended
c) gedit does not come with KDE (KDE's default editor is KATE)
d) to use a custom editor to edit the sudoers file, use ```
EDITOR=/usr/bin/gedit visudo
```

All in all, the above advice is useless at best and dangerous otherwise.

To get back to your problem, what is actually happening with the desktop is "bombing out"?

---

### Post by georgelappies on 2011-03-14
The system startsup to the point where you have to supply login credentials to get into KDE. I enter my username and password. It starts to load the desktop but then goes back to the login screen.

Just before it started doing this I playes around with the 3D desktop settings in the system manager. If I recall correctly there was a tick box to disable opengl compatibility checks. I selected that and since then I could not log back into that account via KDE. The new user I made loads KDE perfectly but he cannot see the home dir of the old user...

---

### Post by prshah on 2011-03-14
> **georgelappies said:**
> startsup to the point where you have to supply login credentials

the 3D desktop settings in the system manager. 

At the login screen, you will find two buttons at the bottom left of the login window (changes depending on your theme). One will be a "power off" style red button, and one will be a blue "down arrow" graphic button. Click the blue button, and choose "Failsafe". Now you should be able to log in as your original user. 

Navigate to the 3D settings (System settings-desktop-advanced) and change it back to the original. Then log out and log back in normally, and everything should be fine.

Please post back with results / errors.

---

### Post by georgelappies on 2011-03-14
> **prshah said:**
> At the login screen, you will find two buttons at the bottom left of the login window (changes depending on your theme). One will be a "power off" style red button, and one will be a blue "down arrow" graphic button. Click the blue button, and choose "Failsafe". Now you should be able to log in as your original user. 


Hi, thanks for your assistance. When I choose failsafe the exact same happens for that user, the new user can login with failsafe without a problem. Weird...

---

### Post by prshah on 2011-03-14
> **georgelappies said:**
> When I choose failsafe the exact same happens 

OK, here's something else you can try:

At the login screen, switch to a virtual terminal with Ctrl+Alt+F1. Log in as the original user, unlock your home directory when prompted.

Now give these commands```
locate kwinrc
mv [color=red]~/.kde/kwinrc[/color] ~/kwinrc_backup
mv .compiz dot_compiz
```

This will remove Kwin and Compiz settings. The first command will give you the location of kwinrc. Please replace this in the second command, instead of the part in red. Depending on whether you used KWin or Compiz, one or the other command may give you an error, which you can ignore (for now).

Now, restart KDE ```
sudo service kdm restart
``` and attempt to log in again (Press Ctrl+Alt+F7..F10 if the login window does not appear).

Please post back with results / errors.

---

### Post by georgelappies on 2011-03-14
:pThanks!!! Problem is solved :)

---

### Post by prshah on 2011-03-14
> **georgelappies said:**
> Problem is solved

Please reboot and check if it logs in normally.

---

### Post by georgelappies on 2011-03-15
> **prshah said:**
> Please reboot and check if it logs in normally.

Thanks yes it is working 100% now. Your assistance is much appreciated :)

---

### Post by highspider on 2011-03-17
> **prshah said:**
> DON'T do this! 
.... 
All in all, the above advice is useless at best and dangerous otherwise.

> **georgelappies said:**
> 
How can I add sudo privileges to the new account (I presume I can do it by logging in with my sudo account in a terminal login?


Sorry missed the [COLOR=Red]KDE[/COLOR] part ](*,). I use Gnome....

But prshah was better with just TTY1  ...
   Didn't mean no harm. 

sudoers info that isn't useless or too dangers 
[http://ubuntuforums.org/showthread.php?t=1132821](http://ubuntuforums.org/showthread.php?t=1132821)

---

