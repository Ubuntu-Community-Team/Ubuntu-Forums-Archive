---
title: "Help please!!! Ubuntu broken"
date: 2010-03-23
forum: General Help
---

### Post by Jiminy555 on 2010-03-23
ok so I did these steps to change my username:


I like to directly edit /etc/passwd and /etc/groups

First open a terminal, become root ```
sudo -i
```Now:

```
usermod -d /home/new -m old

sed -i -e 's_old_new_g' /etc/passwd

sed -i -e 's_old_new_g' /etc/group<-

sed -i -e 's_old_new_g' /etc/shadow
```my computer shut down after I did the second step and now my password isn't working! Please help I cannot open my home folder or get back to root!

---

### Post by Jiminy555 on 2010-03-23
I added the arrow on the second step.

---

### Post by dsiembab on 2010-03-23
ctrl-alt-backspace to shell prompt if zapping isn't disabled in your xorg.conf
login as root I know nono but its ok setup a user
useradd <your old username> // if your your username is not valid
passwd <username>

ONe question why edit the files by hand?

---

### Post by prodigy_ on 2010-03-23
Reboot, and from Grub menu choose "Ubuntu, Linux <your_kernel_version> (recovery mode)" option. Then you'll be able to drop to a root shell. (Since you know how to use sed, I suppose you also know how to open passwd in nano.)

---

### Post by Jiminy555 on 2010-03-23
How do i make new user i dont have password?

---

### Post by Jiminy555 on 2010-03-23
> **prodigy_ said:**
> Reboot, and from Grub menu choose "Ubuntu, Linux <your_kernel_version> (recovery mode)" option. Then you'll be able to drop to a root shell. (Since you know how to use sed, I suppose you also know how to open passwd in nano.)
I dont i was following directions in another thread

---

### Post by prodigy_ on 2010-03-23
```
useradd <login_name>
```
to create a new user.
```
passwd <login_name>
```
to set a password for this user.

---

> I dont i was following directions in another thread
Damn, this forum needs heavier moderation. Suggesting newbies to edit /etc/passwd with sed is just plain destructive.

---

### Post by Jiminy555 on 2010-03-23
> **prodigy_ said:**
> ```
useradd <login_name>
```to create a new user.
```
passwd <login_name>
```to set a password for this user.

---


Damn, this forum needs heavier moderation. Suggesting newbies to edit /etc/passwd with sed is just plain destructive.
useradd: cannot lock /etc/passwd; try again later.


How do I do the Recovery thing?

---

### Post by prodigy_ on 2010-03-23
Ahh, so you're not in a root shell yet. Like I said earlier: reboot, at startup press Shift to get Grub menu, from Grub menu select recovery mode. The OS will boot in single-user mode and you'll see another menu with an option to use root shell. There you'll be able to use "useradd" and "passwd" commands.

---

### Post by Jiminy555 on 2010-03-23
> **prodigy_ said:**
> Ahh, so you're not in a root shell yet. Like I said earlier: reboot, at startup press Shift to get Grub menu, from Grub menu select recovery mode. The OS will boot in single-user mode and you'll see another menu with an option to use root shell. There you'll be able to use "useradd" and "passwd" commands.
I made a new account but i can't do anything because it says Nautilus is wrong or something!  Please I need help I can't add a password to my main account because it says failed! ](*,)

---

### Post by Jiminy555 on 2010-03-23
please help

---

### Post by Jiminy555 on 2010-03-23
> **Jiminy555 said:**
> please help
please

---

### Post by Jiminy555 on 2010-03-23
> **Jiminy555 said:**
> please
anyone?

---

### Post by Jiminy555 on 2010-03-23
please help

---

### Post by Jiminy555 on 2010-03-23
Anyone please, just tell me how to life restrictions and I can just copy all my files and reinstall ubuntu.

---

### Post by Jiminy555 on 2010-04-07
Ok so I did these steps to change my username:

First open a terminal, become root       Code:
     sudo -i 
 Now:
 
      Code:
     usermod -d /home/new -m old

sed -i -e 's_old_new_g' /etc/passwd

sed -i -e 's_old_new_g' /etc/group<-


sed -i -e 's_old_new_g' /etc/shadow 
 

Now when I try to log in it says 


[LIST]
[*]Could not update ICEauthority file /home/JC/.ICEauthority
[*]There is a problem with the configuration server (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)
[/LIST]

[LIST]
[*]Nautilus could not create the following required folders: /home/JC/ Desktop, /home/JC/.nautilus Before running Nautilus, please creat these folders or set permissions such that Nautilus can create them
[/LIST]

Please help me fix this!

---

### Post by -humanaut- on 2010-04-07
Try changing the permissions on it chmod 600

---

### Post by Jiminy555 on 2010-04-07
> **-humanaut- said:**
> Try changing the permissions on it chmod 600
I don't understand; I'm a noob. I followed those steps from another thread.

---

### Post by falconindy on 2010-04-07
verify that your old home directory was moved correctly by usermod.

---

### Post by Jiminy555 on 2010-04-07
> **falconindy said:**
> verify that your old home directory was moved correctly by usermod.
How do I do that?

---

### Post by Jiminy555 on 2010-04-08
> **Jiminy555 said:**
> How do I do that?
anyone?

---

### Post by Rasa1111 on 2010-04-08
he just said he was a noob, 
and you guys are throwing cryptic , partial sentences at him. wth?
I dont think that will help any noob. 

jus sayin. 

 help will be along man, 
just not from me. lol  :popcorn:

g'luck.

---

### Post by uRock on 2010-04-08
```
chmod 600 ~/path to file
```

---

### Post by Jiminy555 on 2010-04-08
> **uRock said:**
> ```
chmod 600 ~/path to file
```
what's the file path?

and i changed my username but my home file is sitll under the old name.  How do i change it and will that fix the problem?

---

### Post by uRock on 2010-04-08
> **Jiminy555 said:**
> what's the file path?

and i changed my username but my home file is sitll under the old name.  How do i change it and will that fix the problem?

Being the home directory, you should be able to just enter the your new account name. I have never changed the name of the Home folder. If I were to try, I would run ```
gksudo nautilus
``` in a terminal, then navigate to the folder in which you want to change the name of. I am not sure if this will work. 

I checked with some friends and they said it would have been easier to just create a new account then copy the files to it. Which is still possible.

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

PS On some threads on this subject, the opinion is that starting certain GUI tools from CLI with sudo may actually cause the problem...

---

### Post by Jiminy555 on 2010-04-08
> **uRock said:**
> Being the home directory, you should be able to just enter the your new account name. I have never changed the name of the Home folder. If I were to try, I would run ```
gksudo nautilus
``` in a terminal, then navigate to the folder in which you want to change the name of. I am not sure if this will work. 

I checked with some friends and they said it would have been easier to just create a new account then copy the files to it. Which is still possible.
ok i'm just going to reinstall ubuntu because when I make a new account and try to log in it says the three bullets i mentioned before.  All i need to know how to do is copy these folders because it says: "You do not have the permissions necessary to view the contents of "KEEP THIS FOLDER".  When I try to view it.  I'm using a Guest account with limited permissions i guess.

[[IMG]http://img208.imageshack.us/img208/7180/screenshotdj.th.png[/IMG]](http://img208.imageshack.us/i/screenshotdj.png/)

---

### Post by Rasa1111 on 2010-04-08
i think you can just copy them onto a flash drive.
will that suffice?

---

### Post by Jiminy555 on 2010-04-08
> **Rasa1111 said:**
> i think you can just copy them onto a flash drive.
will that suffice?
I can't because I don't have permission:(s to read it

---

### Post by bhencetotozo on 2010-04-08
> **Jiminy555 said:**
> Ok so I did these steps to change my username:

First open a terminal, become root       Code:
     sudo -i 
 Now:
 
      Code:
     usermod -d /home/new -m old

sed -i -e 's_old_new_g' /etc/passwd

sed -i -e 's_old_new_g' /etc/group<-


sed -i -e 's_old_new_g' /etc/shadow 
 

Now when I try to log in it says 


[LIST]
[*]Could not update ICEauthority file /home/JC/.ICEauthority
[*]There is a problem with the configuration server (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)
[/LIST]

[LIST]
[*]Nautilus could not create the following required folders: /home/JC/ Desktop, /home/JC/.nautilus Before running Nautilus, please creat these folders or set permissions such that Nautilus can create them
[/LIST]

Please help me fix this!

Hello... If you were renaming your user name... There is an easyer way...

1)First you Log Out off the account you want to rename:
2)press ALT+CONTROL+F1 while in the login screen
3)When it promts for the username to login, follow step 4
4)root
5)password for root
6)usermod -l newusername oldusername


.... That way you should have no BUG... But, if you did it a different way and you got a bug, type this:

inside Control+ALT+F1

sudo chmod 644 /home/username/.ICEauthority

I hope it works, good luck

---

### Post by JoelOl75 on 2010-04-09
Changing the username is NOT an easy thing to do, especially for a noob.  It breaks ALOT of things including the Home directory, sudo, samba permissions, nfs permissions.....


It can be done, but honestly reinstalling is easier.

If someone disagrees try it yourself and see!

You will need to create a root account, then a new user with the right name (Now user 1001) Delete the old user (1000) noting all the groups the 1000 user belongs to.  chown the old users home directory and edit.....

ugghh.. I remember doing this, but the lesson to be had is when installing ubuntu make sure the 1st users name is right and that IT WILL NEVER CHANGE.

---

### Post by bhencetotozo on 2010-04-09
> **JoelOl75 said:**
> Changing the username is NOT an easy thing to do, especially for a noob.  It breaks ALOT of things including the Home directory, sudo, samba permissions, nfs permissions.....


It can be done, but honestly reinstalling is easier.

If someone disagrees try it yourself and see!

You will need to create a root account, then a new user with the right name (Now user 1001) Delete the old user (1000) noting all the groups the 1000 user belongs to.  chown the old users home directory and edit.....

ugghh.. I remember doing this, but the lesson to be had is when installing ubuntu make sure the 1st users name is right and that IT WILL NEVER CHANGE.


I agree... but if you use my method, it will change the login name, but NOT the home directory name... ... i dont think it's ever necessary to change the home/username because its easy to remember.

---

### Post by Jiminy555 on 2010-04-09
Please cans omeone tell me how to unlock the folders

---

### Post by uRock on 2010-04-09
> **Jiminy555 said:**
> Please cans omeone tell me how to unlock the folders

```
gksudo nautilus
``` In a terminal will open a file manager with root privileges. Navigate it to the folders in which you want to change the permissions on and right click the said folder and change its permissions.

---

### Post by Jiminy555 on 2010-04-09
> **uRock said:**
> ```
gksudo nautilus
``` In a terminal will open a file manager with root privileges. Navigate it to the folders in which you want to change the permissions on and right click the said folder and change its permissions.
ugh it says warning cannot open when I try to open in recovery mode

then I can't open it in terminal cause i dont have permission >.<

---

### Post by uRock on 2010-04-09
You may be able to do all of this from the LiveCD.

---

### Post by Jiminy555 on 2010-04-09
mwuhaha i got it to work i just repeated the first to steps i did before!! only problem is i'm not allowed to change the system configuration when i press anything in System>Administration?

---

### Post by uRock on 2010-04-10
Why didn't you ask a mod to merge your threads?

After 2 weeks, I would have booted the liveCD, created another partition to put the data in or copied to an external source then completely reinstalled.

---

### Post by Jiminy555 on 2010-04-10
> **uRock said:**
> Why didn't you ask a mod to merge your threads?

After 2 weeks, I would have booted the liveCD, created another partition to put the data in or copied to an external source then completely reinstalled.
even when i did the cd it wouldn't let me copy the files because i didnt have permission :( I got pictures in there man

---

### Post by cariboo on 2010-04-10
Please don't create multiple threads on the same subject.

---

### Post by Jiminy555 on 2010-04-10
okay just need to gain permissions back now if it's easy

---

### Post by uRock on 2010-04-10
Can you change the user name to get it to match the name on the home folder?

That is the only thing I can think of.

---

### Post by Jiminy555 on 2010-04-10
> **uRock said:**
> Can you change the user name to get it to match the name on the home folder?

That is the only thing I can think of.
that's what i did and it worked, i can log in now but still don't have permissions :confused:  ill try some other stuff

---

### Post by uRock on 2010-04-10
> **Jiminy555 said:**
> that's what i did and it worked, i can log in now but still don't have permissions :confused:  ill try some other stuff

The gksudo nautilus should work for you now. Once you get the permissions straight. Make some backups of your data. This is something we have to do every time we unload our cameras and such, so that when things go wrong, we can fix them quicker and easier.

---

