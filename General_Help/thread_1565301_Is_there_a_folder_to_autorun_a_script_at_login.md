---
title: "Is there a folder to autorun a script at login"
date: 2010-08-31
forum: General Help
---

### Post by CaptainMark on 2010-08-31
I remember reading something a while back that theres a folder that you can just plonk a bash script into and it will run on login but cant find anything about it now.

I have found the command $update-rc.d <filename>
but scripts added this way have to lsbInit compliant and i havent got a clue where to start with that

I also cant just add it to the startup applications list because for some stupid reason following the kernel update a few weeks back (this used to work fine) suddenly has no effect. Heres the script incase anyone wants extra points for telling me why all of a sudden it doesnt work. (ive also made the same script run as a python3 program to no effect.)```
#! /bin/bash
# This is a simple bash script to automatically play a 
# random song on banshee 15 seconds after startup

sleep 15 && banshee --play
```Please help as its one of those small things that has me pulling my hair out, I want my music to start on its own.

---

### Post by libssd on 2010-08-31
I believe the file you want is /etc/rc.local

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0
```
Note that /etc/rc.local is owned by root, so you will need to use sudo to edit it; *e.g*. **sudo gedit /etc/rc.local**

---

### Post by bodhi.zazen on 2010-08-31
> **libssd said:**
> I believe the file you want is /etc/rc.local

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0
```Note that /etc/rc.local is owned by root, so you will need to use sudo to edit it; *e.g*. **sudo gedit /etc/rc.local**


rc.local runs as root as a part of the boot process. Not the same thing as running a script when a user logs in.

Personally I put the script in ~/bin 

To run it at log in you should be able to add it from the gui.

If it is not working, what happens if you run the script from the command line ?

As an aside, I suggest you use the full path to binaries in your script.

---

### Post by CaptainMark on 2010-08-31
So if I add```
bash ~/Documents/scripts/banshee\ autoplay
```above the exit0 line then the script banshee autoplay in ~/Documents/scripts should run, lets give that a try.

---

### Post by bodhi.zazen on 2010-08-31
Use /home/your_user_name and not ~

I would assume rc.local will not work as banshee is a graphical application, but I am not sure.

---

### Post by CaptainMark on 2010-08-31
yeah hadnt thought of that it might try putting the characters ~/ straight in.
the bad news is that just adding the effective line from the script to rc.local doesnt work but
@ bodhi.zazen if i run the line in a terminal it does exactly what id expect it to do sleep&play

---

### Post by libssd on 2010-08-31
bodhi.zazen is truly one of the the Ubuntu gurus. It's an honor to be corrected by him, and I was misunderstanding the question as applying to the startup process, rather than being tied to a user login. 

But, as long as we're on this topic, what about adding something to /home/username/.profile?

---

### Post by CaptainMark on 2010-09-03
what is this file for?

---

### Post by libssd on 2010-09-03
> **CaptainMark said:**
> what is this file for?
/home/username/.profile? 

Not the best definition, but it's a hidden file that is associated with your account, and defines your working environment. It can be personalized from the default version with aliases, and other tweaks.

---

### Post by bodhi.zazen on 2010-09-04
> **libssd said:**
> /home/username/.profile? 

Not the best definition, but it's a hidden file that is associated with your account, and defines your working environment. It can be personalized from the default version with aliases, and other tweaks.

See also :

[http://www.heimhardt.com/htdocs/bashrcs.html](http://www.heimhardt.com/htdocs/bashrcs.html)

[http://www.linuxfromscratch.org/blfs/view/cvs/postlfs/profile.html](http://www.linuxfromscratch.org/blfs/view/cvs/postlfs/profile.html)

You can use these files ( .bashrc , .profile) to customize your environmental variables, bash options, and / or alises. You can use them to start or run applications on log in and log out.

---

