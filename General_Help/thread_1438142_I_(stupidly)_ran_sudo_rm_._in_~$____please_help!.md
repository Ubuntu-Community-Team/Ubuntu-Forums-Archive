---
title: "I (stupidly) ran sudo rm .* in ~$    please help!"
date: 2010-03-24
forum: General Help
---

### Post by wilnd on 2010-03-24
Hello,
 
As you have guessed I am a complete beginner... 
 
I was trying to remove a folder with files in another directory and forgot to write it, so I wrote the command directly from my ~$ home folder. I guess this will teach me to re-read my commands to check they are correct...
 
The console warned me it would not delete many things because they were folders, not files, but I am now wondering what files I have actually deleted that might be vital to my system? I have kept the system up and running, lest it should not boot again if I shut the computer down (not sure if it would be the case but...).
 
Please, help?
 
Thank you!

---

### Post by l.billon on 2010-03-24
Hi!
Do you have any backup of those files? It would be by far the easiest solution...

---

### Post by wilnd on 2010-03-24
Hi,
 
Thanks for replying so fast.
 
No, the system is brand new I had just installed it and I had absolutely no personnal files on the system.
 
I was installing drupal files on LAMP when this happened.
 
I am just worried I might have corrupted the OS in itself and would like to avoid a full re-install.
 
Does the ~$ home usually store anything vital?
 
Thanks!

---

### Post by whoop on 2010-03-24
Your system is fine.. Your account is messed up, you deleted all account configuration (for every application including gnome itself)... Probably not even possible to login with that account any more.

What I would do is create a new user (a new account)... Copy over useful files from the trashed account, remove the trashed account. Continue using ubuntu with the new account.

Restoring from backup is probably the best solution, but not everybody does this (backing up, that is)...


Removing stuff from home is only hazardous for the account you remove it from, not the system itself...

---

### Post by l.billon on 2010-03-24
Actually, only applications use your /home folder to store their settings, the system files are stored in the other directories. 
However, i advise you to wait for another reply before rebooting.

---

### Post by wilnd on 2010-03-24
Hi Whoop,
 
OK... can you help me to get the information on how to create a new account, please ? 
 
I did not do any backup because the system was just brand newly installed... and I still have to learn how to do this (complete beginner as in... well, I know only that I know nothing).
 
Thanks!

---

### Post by wojox on 2010-03-24
Open you terminal and run this:

```
ls -al
```

Post it back up here, please.

---

### Post by wilnd on 2010-03-24
Hi Wojox,
 
Here is what the listing gives:
 
ls -al
total 1220
drwxr-xr-x 37 ocean ocean 4096 2010-03-24 14:49 .
drwxr-xr-x 4 root root 4096 2010-03-11 04:19 ..
drwx------ 3 ocean ocean 4096 2010-03-21 09:30 .adobe
-rw------- 1 ocean ocean 1036 2010-03-24 14:49 .bash_history
drwx------ 7 ocean ocean 4096 2010-03-24 14:25 .cache
drwx------ 3 ocean ocean 4096 2010-03-11 13:34 .compiz
drwxr-xr-x 7 ocean ocean 4096 2010-03-21 11:02 .config
drwx------ 3 ocean ocean 4096 2010-03-11 04:27 .dbus
drwxr-xr-x 3 ocean ocean 4096 2010-03-21 11:22 Desktop
drwxr-xr-x 2 ocean ocean 4096 2010-03-11 04:27 Documents
drwxr-xr-x 2 ocean ocean 4096 2010-03-11 04:27 Downloads
drwxr-xr-x 2 ocean ocean 4096 2010-03-19 17:01 drupal-6.15
drwxr-xr-x 2 ocean ocean 4096 2010-03-24 14:40 drupal-6.16
-rw-r--r-- 1 ocean ocean 1090616 2010-03-03 16:20 drupal-6.16.tar.gz
drwxr-xr-x 3 ocean ocean 4096 2010-03-19 14:22 .evolution
-rw-r--r-- 1 ocean ocean 167 2010-03-11 04:19 examples.desktop
drwxr-xr-x 2 ocean ocean 4096 2010-03-11 13:32 .fontconfig
drwx------ 5 ocean ocean 4096 2010-03-24 13:45 .gconf
drwx------ 2 ocean ocean 4096 2010-03-24 14:49 .gconfd
drwx------ 8 ocean ocean 4096 2010-03-24 14:25 .gnome2
drwx------ 2 ocean ocean 4096 2010-03-11 04:27 .gnome2_private
drwx------ 2 ocean ocean 4096 2010-03-24 13:45 .gnupg
drwxr-xr-x 2 ocean ocean 4096 2010-03-11 14:12 .gstreamer-0.10
dr-x------ 2 ocean ocean 0 2010-03-24 13:45 .gvfs
drwx------ 3 ocean ocean 4096 2010-03-19 16:56 .local
drwx------ 3 ocean ocean 4096 2010-03-21 09:30 .macromedia
drwx------ 3 ocean ocean 4096 2010-03-24 14:29 .mission-control
drwx------ 4 ocean ocean 4096 2010-03-11 12:36 .mozilla
drwxr-xr-x 2 ocean ocean 4096 2010-03-11 04:27 Music
drwxr-xr-x 2 ocean ocean 4096 2010-03-11 04:27 .nautilus
drwxr-xr-x 2 ocean ocean 4096 2010-03-11 04:27 Pictures
drwxr-xr-x 2 ocean ocean 4096 2010-03-11 04:27 Public
drwx------ 2 ocean ocean 4096 2010-03-24 13:45 .pulse
drwx------ 3 ocean ocean 4096 2010-03-11 15:13 .Skype
drwx------ 2 ocean ocean 4096 2010-03-11 04:27 .ssh
-rw-r--r-- 1 ocean ocean 0 2010-03-24 14:36 .sudo_as_admin_successful
drwxr-xr-x 2 ocean ocean 4096 2010-03-11 04:27 Templates
drwx------ 3 ocean ocean 4096 2010-03-24 14:25 .thumbnails
drwxr-xr-x 2 ocean ocean 4096 2010-03-11 12:42 .update-manager-core
drwx------ 2 ocean ocean 4096 2010-03-11 04:27 .update-notifier
drwxr-xr-x 2 ocean ocean 4096 2010-03-11 04:27 Videos
 
Sorry it took so long, am writing from another computer.

---

### Post by whoop on 2010-03-24
> **wilnd said:**
> Hi Whoop,
 
OK... can you help me to get the information on how to create a new account, please ? 
 
I did not do any backup because the system was just brand newly installed... and I still have to learn how to do this (complete beginner as in... well, I know only that I know nothing).
 
Thanks!
[https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)

If you have nothing useful on the trashed account you do not need to move any files... just create a new account using any of the methods described in the howto...

---

### Post by l.billon on 2010-03-24
Seems that most of your applications' folders are still here! That's hopeful.
Nice that you didn't ran rm with the -r option.

---

### Post by sisco311 on 2010-03-24
> **wilnd said:**
> 
Does the ~$ home usually store anything vital?
 


Nope, just your user settings. 

Restore the default .bashrc, .bash_logout and .profile file:
```
cp /etc/skel/.[a-z]* ~
```

Other applications will (re)create their config files if it's needed.

---

### Post by wilnd on 2010-03-24
> **whoop said:**
> [https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)
 
If you have nothing useful on the trashed account you do not need to move any files... just create a new account using any of the methods described in the howto...
 
Thanks!

---

### Post by whoop on 2010-03-24
> **wilnd said:**
> Hi Wojox,
 
Here is what the listing gives:
 
ls -al
total 1220
drwxr-xr-x 37 ocean ocean 4096 2010-03-24 14:49 .
drwxr-xr-x 4 root root 4096 2010-03-11 04:19 ..
drwx------ 3 ocean ocean 4096 2010-03-21 09:30 .adobe
-rw------- 1 ocean ocean 1036 2010-03-24 14:49 .bash_history
drwx------ 7 ocean ocean 4096 2010-03-24 14:25 .cache
drwx------ 3 ocean ocean 4096 2010-03-11 13:34 .compiz
drwxr-xr-x 7 ocean ocean 4096 2010-03-21 11:02 .config
drwx------ 3 ocean ocean 4096 2010-03-11 04:27 .dbus
drwxr-xr-x 3 ocean ocean 4096 2010-03-21 11:22 Desktop
drwxr-xr-x 2 ocean ocean 4096 2010-03-11 04:27 Documents
drwxr-xr-x 2 ocean ocean 4096 2010-03-11 04:27 Downloads
drwxr-xr-x 2 ocean ocean 4096 2010-03-19 17:01 drupal-6.15
drwxr-xr-x 2 ocean ocean 4096 2010-03-24 14:40 drupal-6.16
-rw-r--r-- 1 ocean ocean 1090616 2010-03-03 16:20 drupal-6.16.tar.gz
drwxr-xr-x 3 ocean ocean 4096 2010-03-19 14:22 .evolution
-rw-r--r-- 1 ocean ocean 167 2010-03-11 04:19 examples.desktop
drwxr-xr-x 2 ocean ocean 4096 2010-03-11 13:32 .fontconfig
drwx------ 5 ocean ocean 4096 2010-03-24 13:45 .gconf
drwx------ 2 ocean ocean 4096 2010-03-24 14:49 .gconfd
drwx------ 8 ocean ocean 4096 2010-03-24 14:25 .gnome2
drwx------ 2 ocean ocean 4096 2010-03-11 04:27 .gnome2_private
drwx------ 2 ocean ocean 4096 2010-03-24 13:45 .gnupg
drwxr-xr-x 2 ocean ocean 4096 2010-03-11 14:12 .gstreamer-0.10
dr-x------ 2 ocean ocean 0 2010-03-24 13:45 .gvfs
drwx------ 3 ocean ocean 4096 2010-03-19 16:56 .local
drwx------ 3 ocean ocean 4096 2010-03-21 09:30 .macromedia
drwx------ 3 ocean ocean 4096 2010-03-24 14:29 .mission-control
drwx------ 4 ocean ocean 4096 2010-03-11 12:36 .mozilla
drwxr-xr-x 2 ocean ocean 4096 2010-03-11 04:27 Music
drwxr-xr-x 2 ocean ocean 4096 2010-03-11 04:27 .nautilus
drwxr-xr-x 2 ocean ocean 4096 2010-03-11 04:27 Pictures
drwxr-xr-x 2 ocean ocean 4096 2010-03-11 04:27 Public
drwx------ 2 ocean ocean 4096 2010-03-24 13:45 .pulse
drwx------ 3 ocean ocean 4096 2010-03-11 15:13 .Skype
drwx------ 2 ocean ocean 4096 2010-03-11 04:27 .ssh
-rw-r--r-- 1 ocean ocean 0 2010-03-24 14:36 .sudo_as_admin_successful
drwxr-xr-x 2 ocean ocean 4096 2010-03-11 04:27 Templates
drwx------ 3 ocean ocean 4096 2010-03-24 14:25 .thumbnails
drwxr-xr-x 2 ocean ocean 4096 2010-03-11 12:42 .update-manager-core
drwx------ 2 ocean ocean 4096 2010-03-11 04:27 .update-notifier
drwxr-xr-x 2 ocean ocean 4096 2010-03-11 04:27 Videos
 
Sorry it took so long, am writing from another computer.

Your missing some crucial stuff (for the account that is). .ICEauthority and .dmrc come to mind.

---

### Post by whoop on 2010-03-24
> **sisco311 said:**
> Nope, just your user settings. 

Restore the default .bashrc, .bash_logout and .profile file:
```
cp /etc/skel/.[a-z]* ~
```

Other applications will recreate their config files if it's needed.

What about .ICEauthority and .dmrc?

---

### Post by wilnd on 2010-03-24
> **whoop said:**
> Your missing some crucial stuff (for the account that is). .ICEauthority and .dmrc come to mind.
 
So, do I recreate another account and erase this one or do I proceed as per Sisco311's post? I am really lost and confused... thanks!
 
<quote> 
Restore the default .bashrc, .bash_logout and .profile file:

Code:
cp /etc/skel/.[a-z]* ~
Other applications will recreate their config files if it's needed. 
</quote>

---

### Post by darolu on 2010-03-24
You should be fine, IIRC .ICEauthority re-generates itself at boot, you can create your own .dmrc file:
```
$ touch .dmrc
```
and just to make sure it has the right permissions:
```
$ chmod 644 .dmrc
```
> Restore the default .bashrc, .bash_logout and .profile file:

Code:
cp /etc/skel/.[a-z]* ~
That sounds right too.

---

### Post by whoop on 2010-03-24
> **wilnd said:**
> So, do I recreate another account and erase this one or do I proceed as per Sisco311's post? I am really lost and confused... thanks!
 
<quote> 
Restore the default .bashrc, .bash_logout and .profile file:

Code:
cp /etc/skel/.[a-z]* ~
Other applications will recreate their config files if it's needed. 
</quote>

I would start with Sisco311's post. That one is easier. My workaround will always work, if all else fails :)

---

### Post by wilnd on 2010-03-24
> **whoop said:**
> I would start with Sisco311's post. That one is easier. My workaround will always work, if all else fails :)
 
Thank you, I will try this right away. I really like Ubuntu so far, hope I can get better at it in the (not so far) future!
 
Thanks again.

---

### Post by sisco311 on 2010-03-24
> **whoop said:**
> What about .ICEauthority and .dmrc?


When you create a new user the home directory is populated with the files from /etc/skel directory. Other files are created by the applications when you first run them. i.e. If .ICEauthority or .dmrc is missing, then it's created next time when you log in.

---

### Post by wilnd on 2010-03-24
> **sisco311 said:**
> Nope, just your user settings. 
 
Restore the default .bashrc, .bash_logout and .profile file:
```
cp /etc/skel/.[a-z]* ~
```
 
Other applications will (re)create their config files if it's needed.
 
How can I check that all is back to normal/complete?
I now get the following after running **ls -al** in ~$:
 
total 1236
 
drwxr-xr-x 37 ocean ocean    4096 2010-03-24 15:59 . 

drwxr-xr-x  4 root  root     4096 2010-03-11 04:19 ..
drwx------  3 ocean ocean    4096 2010-03-21 09:30 .adobe
-rw-------  1 ocean ocean    1036 2010-03-24 14:49 .bash_history

-rw-r--r--  1 ocean ocean     220 2010-03-24 15:59 .bash_logout
-rw-r--r--  1 ocean ocean    3180 2010-03-24 15:59 .bashrc 

drwx------  7 ocean ocean    4096 2010-03-24 14:25 .cache
drwx------  3 ocean ocean    4096 2010-03-11 13:34 .compiz
drwxr-xr-x  7 ocean ocean    4096 2010-03-21 11:02 .config
drwx------  3 ocean ocean    4096 2010-03-11 04:27 .dbus
drwxr-xr-x  3 ocean ocean    4096 2010-03-21 11:22 Desktop
drwxr-xr-x  2 ocean ocean    4096 2010-03-11 04:27 Documents
drwxr-xr-x  2 ocean ocean    4096 2010-03-11 04:27 Downloads
drwxr-xr-x  2 ocean ocean    4096 2010-03-19 17:01 drupal-6.15
drwxr-xr-x  2 ocean ocean    4096 2010-03-24 14:40 drupal-6.16
-rw-r--r--  1 ocean ocean 1090616 2010-03-03 16:20 drupal-6.16.tar.gz

-rw-------  1 ocean ocean      16 2010-03-24 15:38 .esd_auth 

drwxr-xr-x  3 ocean ocean    4096 2010-03-19 14:22 .evolution
-rw-r--r--  1 ocean ocean     167 2010-03-11 04:19 examples.desktop
drwxr-xr-x  2 ocean ocean    4096 2010-03-11 13:32 .fontconfig
drwx------  5 ocean ocean    4096 2010-03-24 13:45 .gconf

drwx------  2 ocean ocean    4096 2010-03-24 15:36 .gconfd 

drwx------  8 ocean ocean    4096 2010-03-24 14:25 .gnome2
drwx------  2 ocean ocean    4096 2010-03-11 04:27 .gnome2_private
drwx------  2 ocean ocean    4096 2010-03-24 13:45 .gnupg
drwxr-xr-x  2 ocean ocean    4096 2010-03-11 14:12 .gstreamer-0.10
dr-x------  2 ocean ocean       0 2010-03-24 13:45 .gvfs
drwx------  3 ocean ocean    4096 2010-03-19 16:56 .local
drwx------  3 ocean ocean    4096 2010-03-21 09:30 .macromedia
drwx------  3 ocean ocean    4096 2010-03-24 14:29 .mission-control
drwx------  4 ocean ocean    4096 2010-03-11 12:36 .mozilla
drwxr-xr-x  2 ocean ocean    4096 2010-03-11 04:27 Music
drwxr-xr-x  2 ocean ocean    4096 2010-03-11 04:27 .nautilus
drwxr-xr-x  2 ocean ocean    4096 2010-03-11 04:27 Pictures

-rw-r--r--  1 ocean ocean     675 2010-03-24 15:59 .profile 

drwxr-xr-x  2 ocean ocean    4096 2010-03-11 04:27 Public
drwx------  2 ocean ocean    4096 2010-03-24 13:45 .pulse
drwx------  3 ocean ocean    4096 2010-03-11 15:13 .Skype
drwx------  2 ocean ocean    4096 2010-03-11 04:27 .ssh
-rw-r--r--  1 ocean ocean       0 2010-03-24 14:36 .sudo_as_admin_successful
drwxr-xr-x  2 ocean ocean    4096 2010-03-11 04:27 Templates
drwx------  3 ocean ocean    4096 2010-03-24 14:25 .thumbnails
drwxr-xr-x  2 ocean ocean    4096 2010-03-11 12:42 .update-manager-core
drwx------  2 ocean ocean    4096 2010-03-11 04:27 .update-notifier
drwxr-xr-x  2 ocean ocean    4096 2010-03-11 04:27 Videos

---

### Post by sisco311 on 2010-03-24
> **wilnd said:**
> How can I check that all is back to normal/complete?


Once again, by default, a user's home directory is empty or it's populated with the files from /etc/skel (by default: .bashrc, .bash_logout, .profile and examples.desktop). 

So you should be fine, if an application misses its config file, it will create it.

---

### Post by wilnd on 2010-03-24
> **sisco311 said:**
> Once again, by default, a user's home directory is empty or it's populated with the files from /etc/skel (by default: .bashrc, .bash_logout, .profile and examples.desktop). 
 
So you should be fine, if an application misses its config file, it will create it.
 
OK, that's wonderful. :D
 
Thank you very much!

---

### Post by mysterian077 on 2010-03-24
You might try cp **-r** /etc/skel/.[a-z]* ~

This should copy all folders and files, as if you did create a new user account. It shouldn't overwrite data you have in your account, but you shouldn't have to worry about that anyway.

The . before the * in your original command may have saved you, though if you were not sudo, you shouldn't have to worry about the * matching ..

Good luck with your account!

---

### Post by wilnd on 2010-03-24
Thank you All for your much appreciated help and answers!

---

### Post by sisco311 on 2010-03-24
> **wilnd said:**
> Thank you All for your much appreciated help and answers!

You're welcome!

Please mark your thread as [SOLVED] by selecting **Mark this thread as solved** from the [color="Red"]Thread tools[/color].

---

