---
title: "Can't get past the login screen"
date: 2011-07-15
forum: General Help
---

### Post by azukibeanx on 2011-07-15
At the login screen there's a message saying Install Problem! The configuration defaults for GNOME Power Manager have not been installed correctly. Please contact your computer administrator.
 
I'm the only person who has an account on this computer so I am the only person to log in. In my Passwords and Encryption keys, there is the login password but nothing else. I haven't changed my password but when I enter it in, there is a blank screen with a flashing underscore in the top right corner of the screen but then after a moment it'll return back to the login screen (which isn't purple/orange like it used to be).
 
I am able to get into the terminal, but I have no idea how to tackle this. Help is appreciated.

---

### Post by briealeida on 2011-07-15
You might want to try some of the things here:

[http://forums.fedoraforum.org/showthread.php?t=226569](http://forums.fedoraforum.org/showthread.php?t=226569)

The 'chmod 777 /tmp' fix is not Fedora-specific.

To reconfigure gnome-power-manager, I believe  you could try something like

'dpkg-reconfigure gnome-power-manager'

For both of those commands, you'll need to either be root or prefix them with 'sudo '

---

### Post by azukibeanx on 2011-07-15
> **briealeida said:**
> You might want to try some of the things here:
 
[http://forums.fedoraforum.org/showthread.php?t=226569](http://forums.fedoraforum.org/showthread.php?t=226569)
 
The 'chmod 777 /tmp' fix is not Fedora-specific.
 
To reconfigure gnome-power-manager, I believe you could try something like
 
'dpkg-reconfigure gnome-power-manager'
 
For both of those commands, you'll need to either be root or prefix them with 'sudo '
 
I tried both those things but neither worked... Apparently I don't have "yum" which I tried to install but that doesn't work... I have to be root but I don't have the root password. "sudo dpkg-reconfigure gnome-power-manager" yields nothing. When I try to sudo apt-get install yum, it fails to get some archives and then says "maybe run apt-get update or try with --fix-missing" Fix missing doesn't work and sudo apt-get update (because I'm not root apparently) fails to fetch everything because it could not resolve 'us.archive.ubuntu.com'
 
I am very confused :/ sorry.

---

### Post by Blasphemist on 2011-07-15
Don't try to use yum with ubuntu. That isn't the package manager that ubuntu uses. sudo makes you a super user and your password is likely the right password for it. When you prefix a command with sudo you should be prompted for a password. Are you not? You should then type in the password but it won't display on the screen. After you enter the password and press enter, the command should run.

---

