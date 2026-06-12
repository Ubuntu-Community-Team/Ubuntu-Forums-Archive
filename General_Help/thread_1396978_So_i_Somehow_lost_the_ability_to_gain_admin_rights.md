---
title: "So i Somehow lost the ability to gain admin rights..."
date: 2010-02-02
forum: General Help
---

### Post by GuyZerO on 2010-02-02
I honestly don't know what to do...

I am semi new to linux and i was getting the hang of it until just recently.  i'm trying to do some web design using php and mysql.

in my reference material (the all in one desktop reference {for dummies}).
At some point i needed to do something in /var/www but i ran into a permissions problem so i typed 

```
 chgrp -v -r guy0203 /var/www
  405  chgrp -v -R guy0203 /var/www
  406  chown -v -R guy0203 /var/www
```
afterwards in some subsequent step  it suggested putting the files in /usr/src/mysql. since i didn't have that folder i used mkdir and created it.

then i tried adding the files i needed to that folder and got denied on the grounds of not having permissions once again

so tried something like this

```
 451  chmod 777 /usr/
  452  sudochmod 777 /usr/
  453  sudo chmod 777 /usr/
```It was a 755 originally but i couldn't copy those commands

it turns out as that i had two terminals open in different desktops. one of them was a root terminal. it was at this point that  realized that i was in that root terminal and decided i was done 'learning' for the day. 

i decided to listen to some music (which is located in my windows partion) and ran into a problem. the prompt that pops up to normally asks me for my admin PW to mount the drive. now just vibrates like an incorrect entry was received, says authentication error and says im not authorized to mount that drive

then i went back to terminal to fix it, and when i tried to elevate myself to SU 

i got this
```
guy0203@guy0203-laptop:~$ sudo su
sudo: must be setuid root
guy0203@guy0203-laptop:~$ 
```

i dont know what to do now but i think i totally killed this OS. if so is there anyway to save things if i have to reinstall? 
And if not how can i fix this

(Sorry for being so wordy)

---

### Post by Iowan on 2010-02-02
**sudo su** may be the problem. I've seen another way to do it - I'm trying to look it up (**-i** comes to mind - but not exactly that, either)

Several options listed [here]("https://help.ubuntu.com/community/RootSudo").

---

### Post by warfacegod on 2010-02-02
> 
Code:

 chgrp -v -r guy0203 /var/www
  405  chgrp -v -R guy0203 /var/www
  406  chown -v -R guy0203 /var/www



Shouldn't that first line have -R not -r?

---

### Post by samantha_ on 2010-02-02
boot into recovery mode and run
```
gpasswd -a _username_ admin

```

---

### Post by GuyZerO on 2010-02-03
> **warfacegod said:**
> Shouldn't that first line have -R not -r?

really and truly yes. i did mention i was a beginner

Ok i and i'll google how to boot into recovery mode also... but thanks ill let you know if it works.

---

### Post by GuyZerO on 2010-02-03
alright so i realized i know how to get to the recovery mode. i did that, typed in ```
gpasswd -a guy0203 admin 
```and it didnt work. it says i was added to the admin group but  i still cant mount my hard drive or use sudo for anything.

im utterly impressed with my level of failure... 
what should i do now?

---

### Post by warfacegod on 2010-02-03
Open a Terminal:

```
gksudo users-admin
```

Highlight your user name and click Properties> User Privileges> check "Administer The System".

---

### Post by warfacegod on 2010-02-03
If doing the above won't work from your account:

Reboot and go into the Recovery Console> select "drop to shell"> at the prompt type startx, hit enter:

This will bring you into the root user account. In the Terminal:

```
users-admin
```

and then finish the instructions in my last post.


[B][U][SIZE="3"]
WARNING:[/SIZE][/U][/B] Be very careful of what you do in the root account. It has near god like power and it can be *very* easy to break your system while there. I do not recommend going online while in there unless you absolutely *must*.

---

### Post by GuyZerO on 2010-02-03
so it tried that and it didnt work... i checked admin and everything and i and it still didnt work. i even created another user with the rights i wanted to have and nothing.
i tested by opening a terminal (from root) and su'ing into both accounts and neither can use sudo or have admin rights. i cant even su back to root
i think at this point i at least know what isnt the problem...

---

### Post by Lykopis on 2010-02-04
If all else fails and you must start over, go get a copy of Puppy Linux and burn it to a CD.
 Boot with Puppy and use a USB drive to back up your data files before a reinstall.
 I have done this many times for people who crashed a system.
It works with just about any PC, windoze or Linux.

---

### Post by jocko on 2010-02-04
I'm pretty sure this is what messed it up:> **GuyZerO said:**
> ```
sudo chmod 777 /usr/
```At least if you had an "-R" in the command, it would have changed permissions on some files that won't work with the wrong permissions.
Quick and easy fix: Back up and reinstall. And: next time a command gives you a permission problem, DO NOT CHANGE THE PERMISSIONS of system folders/files; just use sudo in front of the command instead.
Hard and slow fix: google for the correct permissions of every single file you have changed permissions on and change them back...
First thing would be to check the permissions on /usr/bin/sudo and /usr/bin/gksu, and change them back to 755 (-rwxr-xr-x) if they are wrong.

---

