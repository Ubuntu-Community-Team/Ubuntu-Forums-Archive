---
title: "Moved /home, can not log in"
date: 2011-03-18
forum: General Help
---

### Post by Yumi on 2011-03-18
I moved my /home directory to a seperate partition /dev/sda4 . 

When I boot, the login appears and is functional but it does not open the desktop and returns to the login screen.

To me it seems it can not find the /home directory. I added the line > /dev/sda4 /home ext4 nodev,nosuid 0 2 to /etc/fstab.

Have followed every thread I could find to no avail. Any suggestions? My guess is it is something very simple which I overlook.

Michael

---

### Post by seawolf167 on 2011-03-18
Here is the [official how-to ]("https://help.ubuntu.com/community/Partitioning/Home/Moving")for moving your home partition, see if that helps you at all

---

### Post by Yumi on 2011-03-19
I noticed a error message displayed for a short time between GRUB and the LOGIN Page
...... failed to open /dev/null ......

Why does it look for /dev/null and where can the right destination be specified. Is this where fstab is read?

Michael

Thanks for the guide. I found it also after I followed another one!

---

### Post by cavalier911 on 2011-03-20
At the lxdm login screen do the following.

Open a Virtual Terminal:
Ctrl+Alt+F2

If you can Login to account.  

```
mount
```

Is /dev/sda4 mounted on /home ?

If yes then make a new clean account:
```
sudo adduser 
```
from virtual terminal.

Go back to lxdm login screen:
Ctrl+Alt+F7

Try to login to the desktop with the new account.

---

### Post by vanadium on 2011-03-20
First make sure indeed that the partition is effectively mounted. You are using device names where you should use UUID's. I wonder why you used the options nodev,nosuid.

My guess is that your new partition is not correctly mounted. Thus, your (now empty) old home directory is what the system sees. It therefore does not find your user profile.

If you cannot login as cavalier911 said (which you probably will not be able to do if there is a problem with that user's home dir), then you can choose "Recovery" in the grub menu, and select "drop to root prompt without networking" or "with networking" even to gain access to your machine. Then you are indeed root.

* Find the UUID of your sda6 partition from the command "sudo blkid"

* Change the line (or perhaps add if it seems not there!) in /etc/fstab to read
```

UUID=.......  /home ext4 defaults 0 2

```

* Mount it with the command
```

mount -a

```
 There should be no error message. An

```

ls /home

```
should list your moved home directory.

---

### Post by Yumi on 2011-03-21
Thanks for the advice but still not working.

The /dev/null issue was my mistake adding an extra line in fstab.
Adding a user from command prompt - no problem but no change to the situation. Changed fstab to defaults - no change.

The problem is before the login screen as on the login screen it already shows the error message ..could not find gnome-power-manager...

From the dot prompt everything works, I can see the /home directory and its contents, the partition is definitly mounted.

All seems to center around gnome. Maybe reinstalling gnome would help?

A few days ago I tried to sudo apt-get remove gnome-power-manager and then reinstalled it again. Also reinstalled gnome desktop. To no avail.

Question: Is there anything in grub which looks for gnome-power-manager?

Michael

---

### Post by vanadium on 2011-03-21
try following the advice of cavalier911 to create a new account and log in there.

---

### Post by Yumi on 2011-03-21
I did follow his advice and had no problems creating the new account from the dot promt. The account is listed when looking in /home. But logging in from the login screen fails.

The problem is definitly between Grub and Login Screen. Maybe a issue of permission when copying the original /home to /dev/sda4

Michael

---

### Post by Lianli on 2011-03-21
If you haven't lost your original home yet, you could try to recopy just using ( cp -a ) minus the ( ) which just preserves permissions an links etc.. I used cp -a to clone my system to another disk as a back up from time to time and works flawlessly.

---

### Post by oldfred on 2011-03-21
You can update permissions & ownership:

Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)
#Replace all instances of username with your login name.
sudo chown username:username /home/username/.dmrc
chmod 644 /home/username/.dmrc
sudo chown username:username /home/username     
chmod 755 /home/username

.ICEauthority errors
[http://ubuntuforums.org/showthread.php?t=1590835](http://ubuntuforums.org/showthread.php?t=1590835)

---

### Post by Yumi on 2011-03-22
All commands suggested executed perfectly - but no change!

Michael

---

### Post by oldfred on 2011-03-22
Found a few more things to try. Note sure what the problem is.

[http://www.absolutelytech.com/2010/04/13/solved-unable-to-boot-due-to-gnome-power-manager-error/](http://www.absolutelytech.com/2010/04/13/solved-unable-to-boot-due-to-gnome-power-manager-error/)

---

### Post by cavalier911 on 2011-03-22
Kill GDM see if startx open desktop.
Open virtual terminal at gdm login:
```
Ctrl+Alt+F2
```
Login 
Stop GDM
```
sudo  service gdm stop
```
```
startx
```

---

### Post by Yumi on 2011-03-24
The link from oldfred described perfectly my problem. Non of the cures worked. I decided to reinstall and went straight to Natty Alpha3 release.

Thank you for all your efforts. 

Michael

---

