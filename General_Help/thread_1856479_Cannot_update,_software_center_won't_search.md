---
title: "Cannot update, software center won't search"
date: 2011-10-08
forum: General Help
---

### Post by toexii on 2011-10-08
Hi all,

Advanced apologies for any wrongdoing, completely new and am quite uncomfortable with the layout of this forum. :popcorn:

The issue: I haven't had any updates in the past two weeks (approx). When I try to update from the system settings I get this message:


> 
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 59 in source list /etc/apt/sources.list (dist parse)'


Another issue, which may be related (or not), Whenever I open the software center and I search for anything, it will just show the searching animation for an infinite amount of time. This happens always, so essentially I cannot install or remove any software (I am no hero with the command line (yet)).

I could really use some help, thanks in advance!

edit: this may have started after I tried installing Java, but I'm not sure.

---

### Post by kamaji792 on 2011-10-08
Hi toexii,

Welcome to the forum.

I'm no expert with update system issues (and I usually use the command line).  It does sound like the **/etc/apt/sources.list** file has been corrupted.

You should be able to open the file browser to go the the **/etc/apt/** directory and then open the file with **gedit**.  You can then see if the particular line is corrupt and see if you can work out what is should be.

Post a copy here and I will see if I can work out what the problem might be.

If you want to edit it try the following in a **Terminal**:
```
sudo nano /etc/apt/sources.list
```

good luck - k

---

### Post by matt_symes on 2011-10-08
Hi

Kamaji792 is right. You have a problem with your sources.list file.

You can use sed to remove the offending line if you want. 

Open a terminal and copy and paste these commands below.

Make a backup copy.
[FONT=monospace]
[/FONT]```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.old
```Enter your password. It will not be echoed to the screen.

Type this to remove the line

```
sudo bash -c "sed '59d' < /etc/apt/sources.list.old > /etc/apt/sources.list"
```Then type this to update.

```
sudo apt-get update
```Kind regards

---

### Post by toexii on 2011-10-08
Thanks guys, I got it to work. 

First I did everything matt_symes said, but that didn't seem to have done anything. I couldn't find any abnormalities on the wrong line either, it looked just like the others. However after deleting it like kamaji972 said everyting seems to work now. My software center searches again and my updates are currently running.

Thanks a lot!

---

### Post by matt_symes on 2011-10-08
Hi

> **toexii said:**
> Thanks guys, I got it to work. 

First I did everything matt_symes said, but that didn't seem to have done anything

That's rather odd. Take a look at this to remove line 10 (i don't have 59 lines in mine as can be seen below).

```

matthew@matthew-laptop:~$ wc -l /etc/apt/sources.list
54 /etc/apt/sources.list
matthew@matthew-laptop:~$ sudo mv /etc/apt/sources.list /etc/apt/sources.list.old
matthew@matthew-laptop:~$ sudo bash -c "sed '10d' < /etc/apt/sources.list.old > /etc/apt/sources.list"
matthew@matthew-laptop:~$ diff /etc/apt/sources.list /etc/apt/sources.list.old
9a10
> deb http://gb.archive.ubuntu.com/ubuntu/ lucid main restricted
matthew@matthew-laptop:~$ 

```Not sure why it would not work for you.

I'm very glad you got it working though :D

Kind regards

---

