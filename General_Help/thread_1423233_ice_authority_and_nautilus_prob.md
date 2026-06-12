---
title: "ice authority and nautilus prob"
date: 2010-03-06
forum: General Help
---

### Post by drjugaljpatel on 2010-03-06
hi Scott,
 Jus gone through your post on the prob you had with 9.10. Am also havin a similar prob, am a new bee and not able to figure out my way through. It would be of great help if you could pull me out through this..

I get the following error,
Unable to update ICEauthority.file/home/drjugaljpatel/.ICEauthority

Followed by by
There is a configuration problem with the configuratiion serverr (/usr/lib/libgconf 2-4/gconf.sanity-check-2 exited with status 256)

Then,
Nautilus colud not create the following required folders :/home/drjugaljpatel/Desktop/home/drjugaljpatel/.nautilus

All am left is a home screen on which nothing is working, tried chown, chmod... Seeing some suggestions... But to no avail.. Gotta a presentation comin up tomo.. So please help me.. Either fix it or recover the data.. Anything will do



hi everyone
  am a new bee and not able to figure out my way through. It would be of great help if you could pull me out through this..

I get the following error,
Unable to update ICEauthority.file/home/drjugaljpatel/.ICEauthority

Followed by by
There is a configuration problem with the configuratiion serverr (/usr/lib/libgconf 2-4/gconf.sanity-check-2 exited with status 256)

Then,
Nautilus colud not create the following required folders :/home/drjugaljpatel/Desktop/home/drjugaljpatel/.nautilus

All am left is a home screen on which nothing is working, tried chown, chmod... Seeing some suggestions... But to no avail.. Gotta a presentation comin up tomo.. So please help me.. Either fix it or recover the data.. Create a new user.. Anything will do

Please help me out..

---

### Post by flippo on 2010-03-06
Can you log in as root? (DON'T log into gnome as root, push ctrl+alt+f1 then log in to tty1 as root, ctrl+altl+f7 will return you to gnome).  

I'm assuming you can (root should not have ICEauthority problems)
please post the output of:```
ls -l /home
ls -al /home/drjugaljpatel | grep ICEauthority
ls -al /home/drjugaljpatel | grep nautilus
```

NOTE: to get these output to a file (so they are easier to post), follow the command with "> filename" 
example:```
ls -l /home/ > homels
```The file homels will be created with the output from the ls command

EDIT: On second thought, you can actually log in as your normal user from tty1, it doesn't use the GUI so it will not need the .ICEauthority file.

---

### Post by drjugaljpatel on 2010-03-06
the output is
Total 20
drwx------ 52 drjugaljpatel drjugaljpatel 20480 2010-03-06 17:01 drjugaljpatel (last word in blue)

-rw-r--r-- 1 drjugaljpatel drjugaljpatel 49368 2010-03-06 20:57 .ICEauthority    (the last word in red)

drwxr-xr-x 2 drjugaljpatel drjugaljpatel 4096 2009-11-16 19:21 .nautilus (again in red)

---

### Post by flippo on 2010-03-06
try:```
mv .ICEauthority .ICEauthoritybup
```
then log into gdm, do you still get the ICEauthority error?

---

### Post by drjugaljpatel on 2010-03-06
means i have to type the code , exit and reboot right

---

### Post by flippo on 2010-03-06
hit ctrl+alt+f7, log out, hit ctrl+alt+f1 log in, type code, ctrl+alt+f7 log in, report if it worked

---

### Post by drjugaljpatel on 2010-03-06
after hitting ctrl + alt + f7 could not logout. No log out soption available. So hit the code, typed logout in tty1 and rebooted, still the same prob..

---

### Post by flippo on 2010-03-06
Including the ICEauthority error?

If so, what is the output of:```
ls -al ~/ | grep ICEauthority
```

---

### Post by drjugaljpatel on 2010-03-06
ya its including iceauthority

Output reads

-rw-r--r--  1 drjugaljpatel drjugaljpatel 49368 2010-03-06 20:57 .ICEauthoritybup

---

### Post by flippo on 2010-03-06
Hmmm, odd.  While, here are my permissions for ICEauthority and my home directory, maybe if you mimic them it will help:

home: 766
ICEauthority 600

to set these:```
sudo mv ~/.ICEauthoritybup ~/.ICEauthority
sudo chmod 766 /home/drjugaljpatel
chmod 600 ~/.ICEauthority
```

If that doesn't work you have something deeper wrong... attach your .xsession-errors file. (please please please put it in an attachment or code block, it will be big...)

---

### Post by sandyd on 2010-03-06
nvm.

---

### Post by drjugaljpatel on 2010-03-06
well, its given out the same prob.. Think it is screwed.. All i did was jus fiddling around with login screen optionss.. 

If you could just let me knoe is it possible to access the files (for backup) through jaunty (have a dual boot, currently shows no permission to access the files of karmic from jaunty). Or is it possible to copy the file onto a pendrive via tty..

 
Thanks a lot..

---

### Post by flippo on 2010-03-06
In a last resort (besides reinstalling) you can make a new user, and copy over all your files to that user.```
sudo useradd <newuser>
sudo passwd <newuser>
```You'll also have to put him in the admin group if you want to sudo```
sudo gpasswd -a <newuser> admin
```.

You can then copy over all of the needed data from the old home folder, etc.

That should solve the issue, but you'll have a new user.

To find out what groups you are in (the new user should be in the same) type "groups" into the terminal as your old user, then use the gpasswd command to add the new user to them.

---

### Post by rnerwein on 2010-03-06
hi
 you said: All you did was jus fiddling around with login screen optionss..
did you have the UMASK settings in /etc/login or have look at /etc/profile - the umask should be 022
ciao

---

### Post by drjugaljpatel on 2010-03-06
i tried adding the new user, it was successful.
But when i reboot, it does not ask for username or password. It is directly logging in with my old login id and the same set of error messages. 
I also hit ctrl+alt+f1, logged in as the new user that i created, then hit ctrl+alt+f7, still am in the old screen only. 

Is it possible to change the login screen details to ask password, rather than the current automatic login. I think thats the crux of the prob, when i  jus selected automatic login, that all the prob started.

---

### Post by flippo on 2010-03-06
Hmmm, I don't know how to disable it without the GUI.  There is another last attempt we can make on your old account to get it running again...

First things first, I'm sure you like gui better than tty1, logon to tty1 and type:```
sudo /etc/init.d/gdm restart
```This should bring up the login screen, where you can login as your new user :)

Second thing:
Lets try to get that old user logging in, at least partially...
We need your old users permissions, lets log in as them:```
su <oldusername>
```
Now, lets move around some config files and see if this helps (it most likely wont, but I think its worth a try)
```
sudo mv /home/<oldusername>/<folder> /home/<oldusername>/<folder>_backup
```

Please replace <oldusername> with whatever your old username was, and replace <folder> with one of the following (You'll have to run the mv command a few times...)

.gconf .gnome .gnome2 .gnome2_private .compiz .themes .icons .nautilus

After you move these folders you'll deactivate all changes your old user had on their gnome-desktop, but if one of those broke it (which it appears it may have) then it'll fix up the old desktop.

Sorry I didn't suggest this earlier, I didn't think of it.

EDIT:
You should also be able to edit the autologin stuff from your new account, if you really don't want to try and recover your old one.

---

### Post by drjugaljpatel on 2010-03-06
i tried adding the new user, it was successful.
But when i reboot, it does not ask for username or password. It is directly logging in with my old login id and the same set of error messages. 
I also hit ctrl+alt+f1, logged in as the new user that i created, then hit ctrl+alt+f7, still am in the old screen only. 

Is it possible to change the login screen details to ask password, rather than the current automatic login. I think thats the crux of the prob, when i  jus selected automatic login, that all the prob started.

---

### Post by flippo on 2010-03-06
try this:
start the pc, wait for the death screen
ctrl+alt+f1
login
```
sudo /etc/init.d/gdm restart
```
gdm login screen *should* popup (I hope)

From there log in as your new user and disable the automatic login with that.

---

### Post by drjugaljpatel on 2010-03-06
hey, the first step worked.. back with my gui.. Everything working fine.. But didnt ask for login,, automatically logged in as old user.. Shall i change the log in settings to ask password

---

### Post by flippo on 2010-03-06
When you typed gdm restart it logged straight in?

---

### Post by drjugaljpatel on 2010-03-06
yes straight in as the old user with complete gui that is functioning.. Think because i had activated the automatic login , after which all this started.

---

### Post by flippo on 2010-03-06
bleh!

I have two more things to try, we can just drop the hammer on it and force it to work! or we can be more subtle:

the more subtle approach:
drop to tty1 (ctrl+alt+f1)
log in as your new user
```
sudo /etc/init.d/gdm stop
startx
```
this SHOULD (I really hope) bring you straight into a gnome-session as your new user (yay) where you can adjust the autologin info!

Dropping the hammer:
drop to tty1
login as new user
```
sudo mv /home/<oldusername> /home/<oldusername>_backup
```
now it will recreate the old user's home directory when gnome logs in (I think) and everything will be back to the default state (like for your new user)

tell me if either (or both) of these work for you.

---

### Post by drjugaljpatel on 2010-03-06
hi, i adjusted the settings to always ask for log in.. Rebooted.. Now its working fine.. Asking for log in option with two users..

Thanks a lot.. Saved my day.. Should i reinstall or jus continue

---

### Post by flippo on 2010-03-06
Well, once your sure you don't need anything out of your old user's home account you can delete it and your old user "sudo userdel <oldusername>" at that point your system is as good as new.  You can reinstall if you want, but I don't see a point.

EDIT:
alternatively:  you can try to overwrite your old user's home directory with your new user's one (once your sure your old user doesn't have anything you need) then you should be able to log in as your old user just as if it were your new user (minus with your old user's password).  You can then delete either user, and life is good.

---

### Post by drjugaljpatel on 2010-03-06
will do that..

Thanks a lot for patiently givin me step by step procedure..

---

### Post by Flos Headford on 2010-04-08
This worked for me:
Use a Ubuntu Live CD to boot up, and choose a command-line (shell) option.
With this, set your $HOME directory (/home/username) permissions to something appropriate (I used 755) and make sure all directories can be listed with the "ls" command. Then remove nautilus with ```
sudo apt-get remove nautilus
``` and delete the .ICEauthority entry in $HOME, and possibly in /var/lib/gdm. Then reboot with ```
sudo shutdown -r now
``` When you choose the same option on boot-up, from the command line you can use ```
sudo apt-get install nautilus
sudo shutdown -r now
``` and retrieve the CD a bit smartish. I do hope you get a clean straight boot and login, as I did!
With thanks to all who helped me,
Phil

---

### Post by sunnykillz on 2010-04-14
i was having same pro but some how i fixed it but now i have a problem that my old desktop is gone.i didnt find my old files.is there  any solution for that?.but some of the files are there like i installed some games from repositories and a software of gnuradio grc.it is working but my desktop files are not there.....can anyone help me.or u can guide me where are the old files saved in ubuntu.if they were on desktop.plz help me cuz those were imp files of my project....

---

### Post by mjcritchie on 2010-04-20
I have had the same problem twice, both times after updating (currently running 64bit Karmic).

Tried various solutions on the net, but this is the only one that worked for me:

Open a terminal and run:

> sudo chown -R user:user /home/user/.*

Where user is your user_name. This should change ownership of all the hidden files and directories in your home directory to: user:user, as they should be.

This comes courtesy of tommcd over at [this]("http://www.linuxquestions.org/questions/ubuntu-63/karmic-9-10-with-separate-home-partition-caused-could-not-update-iceauthority-798084/") post on LinuxQuestions.org

---

### Post by vrubium on 2011-08-20
> **mjcritchie said:**
> I have had the same problem twice, both times after updating (currently running 64bit Karmic).

Tried various solutions on the net, but this is the only one that worked for me:

Open a terminal and run:



Where user is your user_name. This should change ownership of all the hidden files and directories in your home directory to: user:user, as they should be.

This comes courtesy of tommcd over at [this]("http://www.linuxquestions.org/questions/ubuntu-63/karmic-9-10-with-separate-home-partition-caused-could-not-update-iceauthority-798084/") post on LinuxQuestions.org

Thaks man, same thing worked for me!
lot of googling around the forum but it worked :)

thks

---

