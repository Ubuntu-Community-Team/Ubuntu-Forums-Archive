---
title: "Programs that start when Ubuntu boots"
date: 2010-04-10
forum: General Help
---

### Post by pcdave98 on 2010-04-10
Squeezebox Server starts when I boot the PC (regardless of OS) but now, with Ubuntu, it (according to Google) starts too soon. It starts before the wireless network is working. This causes problems "resolving IP addresses" for the wireless radios. My fix is:
 
sudo /etc/init.d/squeezeboxserver stop 
sudo /etc/init.d/squeezeboxserver start
 
How can I delay it starting when I boot?

:)

---

### Post by pcdave98 on 2010-04-10
Come on! Are we letting Squeezeboxserver win?

Of course not.

Help.

:P

---

### Post by nemilar on 2010-04-10
You can change the order in which services load on bootup.

Service starting is controlled by the /etc/rcX.d/ directories, where 'X' is the runlevel number.  You are probably in runlevel three (type the command 'runlevel' to find out).

The /etc/rcX.d/ directories contain symbolic links that are executed in alphabetical order.  For example, something named 'S01something' will be exected before 'S99something'.

You can find the service you want to start last, and rename it so that it the last thing listed in the folder when you do 'ls -1'.

Make sure it starts with 'S' and then a number.

---

### Post by sgosnell on 2010-04-10
Those services aren't startup programs, though.  They won't affect squeezebox or network manager, which are both started after all the services are loaded.  I don't know of a way to control the order in which startup programs are loaded.

---

### Post by pcdave98 on 2010-04-11
OK - thanks for the replies.

Would it be possible for me to create an icon, on my desktop, that would run those two command lines for me?

:)

---

### Post by steveneddy on 2010-04-11
> **nemilar said:**
> You can change the order in which services load on bootup.

Service starting is controlled by the /etc/rcX.d/ directories, where 'X' is the runlevel number.  You are probably in runlevel three (type the command 'runlevel' to find out).

The /etc/rcX.d/ directories contain symbolic links that are executed in alphabetical order.  For example, something named 'S01something' will be exected before 'S99something'.

You can find the service you want to start last, and rename it so that it the last thing listed in the folder when you do 'ls -1'.

Make sure it starts with 'S' and then a number.

I believe this is the correct answer.

---

### Post by sgosnell on 2010-04-11
It's easy enough to create a desktop link that runs a script containing those lines.  Open your favorite text editor, create the script you want, save it, then make a new link to that script.

---

### Post by pcdave98 on 2010-04-16
Thanks all.

I renamed the file, as nemilar suggested, but it's still the same. 

sgosnell - that's exactly what I want to do. I was really asking how to actually do it.

It's not really an issue tbh. Two commands in a terminal window isn't the end of the World.

:)

---

### Post by dcstar on 2010-04-17
> **pcdave98 said:**
> Squeezebox Server starts when I boot the PC (regardless of OS) but now, with Ubuntu, it (according to Google) starts too soon. It starts before the wireless network is working. This causes problems "resolving IP addresses" for the wireless radios. My fix is:
 
sudo /etc/init.d/squeezeboxserver stop 
sudo /etc/init.d/squeezeboxserver start
 
How can I delay it starting when I boot?

:)

/etc/rc.local

---

