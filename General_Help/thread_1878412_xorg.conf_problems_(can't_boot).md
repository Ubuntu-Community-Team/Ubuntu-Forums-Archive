---
title: "xorg.conf problems (can't boot)"
date: 2011-11-09
forum: General Help
---

### Post by zcacogp on 2011-11-09
Hello, 

In trying to make my Ubuntu (KDE front-end) install better I seem to have broken it ... and need some help! 

My machine was working, but the screen was struggling. I suspected a driver problem, so followed the instructions here: 

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

... to identify, download and install a better screen driver. When it was installed I rebooted, and it seemed to boot fine but opening a window caused KDE to crash and return me to the login screen. 

Knowing that I had old versions of xorg.conf in the /etc/X11/ directory, I went into a TTY and tried re-naming old versions in turn and tried booting with them. But not only did I fail to manage to get it to boot, I made things worse. Now, when I boot, I can choose 'Ubuntu' from GRUB, but I never get beyond the purple screen; it hangs before giving me the Ubuntu logo with the five spots. 

I can boot into recovery mode, and get to a root prompt, but if I try to do anything like this: 

# sudo mv xorg.conf.old xorg.conf

I am told "mv: cannot move 'xorg.conf.old' to 'xorg.conf': Read-only file system. I have the same problem if I try to use Nano to edit xorg.conf - it doesn't allow me to save the changed version. 

If I try: 

# sudo X -configure

(which was suggested elsewhere), I am told that there was a fatal server error, Could not create lock file in /tmp/.tX0-lock. If I go into /tmp I find that there is no directory called .tX0-lock, but if I try to create one I am told (again) that it is a read-only directory and therefore it is not permitted. 

I don't know what has changed that made the /etc/X11 directory read-only; five minutes ago I was able to change the names of files in there, now I can't. 

I am therefore at the end of things that I know how to do. There is a similar thread here: 

[http://ubuntuforums.org/showthread.php?t=1453192&page=3](http://ubuntuforums.org/showthread.php?t=1453192&page=3)

... but the guy doing it ended up re-installing. I have tried fsck but am told that the /dev/sda2 partition (Ubuntu system partition) is clean. 

Are there any alternatives other than re-installing? 

(The machine is an AMD64, running Ubuntu 11.10 Oneiric, with both Gnome and KDE as front-ends. The graphics card is an AMD/ATI Radeon 3300 series on-board graphics card. The machine worked with the proprietary driver installed from the "Additional Drivers" tool, but not very well - which is why I was trying to improve it!) 

Thanks very much, in advance, for any help. 


Oli.

---

### Post by zcacogp on 2011-11-10
OK, slight update on this. 

I created a fresh install of Kubuntu on a spare partition, and used this to mount the system disk of the problematical install, and swapped the xorg.conf files around. I am now back to the point where the machine will boot, and I can log in, but the moment I try to open something then KDE crashes and logs me out. 

I can log into the "Failsafe" version of KDE and this works, but desktop effects (amongst others) are lost, and the screen is even worse than before. 

As before, all suggestions are welcome - thanks. 


Oli.

---

### Post by zcacogp on 2011-11-10
OK, more update. And the problem is solved. 

As a point of reference, if anyone else ends up in the same situation I did, the solution is thus; 

- Log into the "Failsafe" system (choose at the login screen
- Follow the instructions here: 

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

... (the one entitled "Problem: Need to fully remove -fglrx and reinstall -ati from scratch") ... and it seems to put your machine back to the just-been-freshly-installed configuration, and it will work again. Be warned that any system settings (to do with screen drivers) you have applied will be lost and will need to be re-applied. 


Oli.

---

### Post by antiplex on 2012-01-23
just for the sake of helping others having a similar issue with ubuntu 11.10: note that if you are getting the error 
```
Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.
```upon the execution of ```
X -configure
``` even when booting into the root-shell of the recovery mode, it could be that a display manager is still running and the way to shut it down on ubuntu 11.10 with unity enabled would be ```
sudo service lightdm stop
```afterwards the comand to re-generate a xorg.conf should work fine.

cheers

edit: pay attention to the output, in my case i almost overlooked the line saying '(++) Using config file: "/home/<username>/xorg.conf.new"'

edit2: weird enough, the second time i tried this i could not get it done through the root-recovery-mode but could CTRL + ALT + 1 and stop lightdm there through 'sudo service lightdm stop' and successfully run 'X -configure' afterwards...

---

