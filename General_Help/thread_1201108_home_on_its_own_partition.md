---
title: "/home on its own partition"
date: 2009-06-30
forum: General Help
---

### Post by rbc on 2009-06-30
I bought a new hard drive a while back, cloned my system over from a 100GB to a 160 GB hard drive, so I now have 60 GB of free space. I would like to finally undertake the task of giving /home its own partition. 
I was going to follow this tutorial to create the /home partition:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
I have already created the partition, used pysdm to mount it at startup, and made myself the owner of the mount point, so hopefully I have not doomed the whole thing to failure by doing things a bit out of order. A couple questions though. Has anyone used that how-to and had success, or is there another process you recommend? And secondly, can someone explain one of the steps to me. Toward the end, there is a series of commands:
cd /old/home
find . -depth -print0 | cpio --null --sparse -pvd /new/
sudo mv /old/home /old/home_backup
sudo mkdir /old/home

Why is there a mkdir command on the. Isn’t there already a directory called /old/home, since we did a cd /old/home in the first command, and then moved /old/home in the third?
And lastly, feel free chime in on the sudo find . -depth -print0 | sudo cpio --null --sparse -pvd /new/ versus  find . -depth -print0 | sudo cpio --null --sparse -pvd /new/ commands
Thanks, in advance, for your time and opinions.

---

### Post by lindsay7 on 2009-06-30
I did this and it worked out great.  Note the line you discussed

> Note: I have tested the second command myself, and it works, but some have pointed out it might make sense to preface the commands with sudo in case one of the other users has subdirectories manually marked as unreadable to the user making the move. Since I have not tested this out and all directories and readable to all by default, I'm offering this as only an alternative in case the command as given does not work:
_sudo find . -depth -print0 | sudo cpio --null --sparse -pvd /new/ _

This work and the other did not.

To answer you question, the instructions say > Now we're going to _back up the /home directory on the old partition and move it to the new _partition:



Also I had to use the part that says ```
Now we're going to back up the /home directory on the old partition and move it to the new partition:

```

But is all worked out fine.   Just make sure you have all your important stuff backed up just in case.  If you do a clean install sometime it is much easier to set up a separate home partition to start with.

---

### Post by michy99 on 2009-06-30
When you do```
sudo mv /old/home /old/home_backup
```you rename /old/home to /old/home_backup. (It doesn't really move anything, just renames it.) So you have to make a new /old/home.

---

### Post by ronaldprettyman on 2009-06-30
**the quick and dirty way**


Format the remaining 60gigs and were assume for that that the partition is /dev/sda3
I would also tell you how to partition your drive from the console but those commands are not allowed in the forums, so your have to use something like gparted from gnome.
ALT+F2 gparted
Format the 60gigs ext3, if you choose another note it as your want to replace ext3 with the format you choose.

Reboot into single usermode
(esc at grub, select recoverymode, or edit the default mode with the e key, and add single the end of the kernel line)
exit to console/shell
Double check that your in single usermode
Note another safe way to do this.
hold ALT+CTRL+F1
Login
Kill gnome and gdm
```
sudo /etc/init.d/gdm stop
```
For some reason this doesn't always work
```
sudo pkill gdm
```
If you choose to do this from single user mode
```
runlevel
```
should see 0
You can always move to single user mode though another command, but I won't share that here as I don't know if it would be taken out of context. (sudo init 0)
Also your notice that in runlevel 0 single user mode your have no need to use sudo for these commands
if you are in single user mode you will not need sudo, but if you kill X, you won't need to be in single user mode.
```
whoami
```
Response, root
**Step 1**
Move the old home folder
```
sudo mv /home /oldhome
```
**Step 2**
Create a new home folder
```
sudo mkdir /home
```
**Step 3**
Add the new partition to your /etc/fstab
```
sudo vi /etc/fstab
```
at this to the end
```
/dev/sda3 /home ext3 relatime,errors=remount-ro 0 1
```
replace /dev/sda3 with the partition your new drive is
and replace ext3 with the type of drive
**Step 4**
Mount the new home folder
```
sudo mount /home
```
You could also test your fstab at this time instead of the above
```
sudo mount -a
```
**Step 5**
Now copy the old home to the new home
```
sudo cp -R --preserve /oldhome/* /home
```
**Step 6**
now double check the home folder
```
sudo ls -l /home
```
and check it against the old folder
```
sudo ls -l /oldhome
```
You should now have your 60 gig drive setup as your new home folder
Just to be completely on the safe side reboot your system before deleting the /oldhome directory, you may keep it as a restore point as well, note that in a new installation after reinstalling all your usual setting you can do steps 1,2,5,6 to bring old user settings into a new installation.
Once your absolutely sure, test each username in home folder(all users except root, which you shouldn't have any way right :p)
You can safely delete the oldhome folder.
```
sudo rm -rf /oldhome
```

---

### Post by rbc on 2009-06-30
Okay. Thanks for the help so far. It did not go as badly as I had feared, but I do have a small problem which is probably a permission issue. All of the desktop icons/launchers lost their pictures. They are rectagukar boxes with writing in them that is too small for these old eyes to read. When I click on one, I get this:

Untrusted Application Launcher

The application launcher "firefox.desktop" has not been marked as trusted. If you do not know the source of this file, launching it may be unsafe

Then three choices:

Launch anyway       Mark as Trusted      Cancel

Marking it as trusted does not fix anything, but it will launch whatever it's supposed to. Creating a new icon/launcher has the same issue.

Full disclosure.....I did get the .dmrc and .ICEauthority problems, and did not know how to get to console from Recovery Mode, so I did a Ctrl + Alt + F1 and did the chown/chmod actions from there.

---

### Post by ronaldprettyman on 2009-07-01
> **rbc said:**
> Okay. Thanks for the help so far. It did not go as badly as I had feared, but I do have a small problem which is probably a permission issue. All of the desktop icons/launchers lost their pictures. They are rectagukar boxes with writing in them that is too small for these old eyes to read. When I click on one, I get this:

Untrusted Application Launcher

The application launcher "firefox.desktop" has not been marked as trusted. If you do not know the source of this file, launching it may be unsafe

Then three choices:

Launch anyway       Mark as Trusted      Cancel

Marking it as trusted does not fix anything, but it will launch whatever it's supposed to. Creating a new icon/launcher has the same issue.

Full disclosure.....I did get the .dmrc and .ICEauthority problems, and did not know how to get to console from Recovery Mode, so I did a Ctrl + Alt + F1 and did the chown/chmod actions from there.
You wanted to do a persistant copy of your old to your new to maintain ownership or it won't work.

Easy fix.

let pretend for this example your username is $USER
(actually if your logged in as yourself $USER is a global variable for the current user and is peristant while in SUDO)
Never take my word for so verify first that $USER is infact your username while sudoing
```
sudo echo $USER
```
output should be your username
Curious enough
```
sudo whoami
```
answer is root
```
sudo chown -R $USER:$USER /home/$USER
```
chown, sets the owners
-R all files and subfolders
$USER:$USER user:group
/home/$USER your home folder
double check
```
ls -l /home/$USER
```
should see
(permissions) # $USER $USER
down the row

LOG OUT, LOG IN as $USER
Everything should be working now

---

### Post by rbc on 2009-07-01
ronaldprettyman, Thanks for the input so far. I actually followed the pyschocats how-to before you responded, but was unable to post back because there was apparently a problem with the servers last night. I did, in fact, do these commands after getting the .dmrc error.

chown -R username:username /home/username
chmod 644 /home/username/.dmrc
chmod 644 /home/username/.ICEauthority
exit

But I did not know how to get to console after booting into recovery mode, so I booted up normally, and did Ctrl + Alt + F1. I did not however, kill gdm and gnome. Is that what caused this problem?

---

### Post by rbc on 2009-07-01
Thank you all for the help. In case this benefits anyone at all.....Thanks to the backup I had, I put everything back to its original state, and started over. The first time around, after I got the .dmrc error, I dropped to command line and did a chmod, and also did chmod for the .ICEauthority file, even though I had not yet had an issue with that (figured if I had one error, I was going to get the other). This second time, I only chmod for .dmrc. I rebooted and all is wonderful. My very own, huge, /home partition. Lessons learned:
1. ALWAYS HAVE A BACKUP, or two
2. Don't try to correct a problem that hasn't presented itself yet

---

### Post by ronaldprettyman on 2009-07-02
> **rbc said:**
> Thank you all for the help. In case this benefits anyone at all.....Thanks to the backup I had, I put everything back to its original state, and started over. The first time around, after I got the .dmrc error, I dropped to command line and did a chmod, and also did chmod for the .ICEauthority file, even though I had not yet had an issue with that (figured if I had one error, I was going to get the other). This second time, I only chmod for .dmrc. I rebooted and all is wonderful. My very own, huge, /home partition. Lessons learned:
1. ALWAYS HAVE A BACKUP, or two
2. Don't try to correct a problem that hasn't presented itself yetYep been down that road before. Its always good to keep lots of backups of anything you can't replace, and delete crap you download off the net that is easy to replace, it makes your backups smaller and easier to manage.
DOUBLE POST PLEASE DELETE Thank you!

---

### Post by ronaldprettyman on 2009-07-02
> **rbc said:**
> Thank you all for the help. In case this benefits anyone at all.....Thanks to the backup I had, I put everything back to its original state, and started over. The first time around, after I got the .dmrc error, I dropped to command line and did a chmod, and also did chmod for the .ICEauthority file, even though I had not yet had an issue with that (figured if I had one error, I was going to get the other). This second time, I only chmod for .dmrc. I rebooted and all is wonderful. My very own, huge, /home partition. Lessons learned:
1. ALWAYS HAVE A BACKUP, or two
2. Don't try to correct a problem that hasn't presented itself yetYep been down that road before. Its always good to keep lots of backups of anything you can't replace, and delete crap you download off the net that is easy to replace, it makes your backups smaller and easier to manage.

Also note you can reinstall linux and bring in your home folder with you, you can also bring it between different distribution with little complaint. All your personal settings are stored in hidden files (files that begin with a .) in your home folder, so its really the only thing you NEED to backup and the only place you should put personally things. Its also good to add a bin folder to your home folder for your personal scripts as well. Then just add it to your path in your profile. So your bookmarks, im accounts, emails accounts, desktop, taskbars and everything (other then installed software, with the exception of things installed to your home folder) come with you when you bring you home folder.

export $PATH=$PATH:~/bin

---

