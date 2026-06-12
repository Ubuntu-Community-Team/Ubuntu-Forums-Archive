---
title: "about apt-get"
date: 2011-04-11
forum: General Help
---

### Post by HaRabAS on 2011-04-11
look at this:

[IMG]http://i105.photobucket.com/albums/m226/harabas/ss32.png[/IMG]

and i wasn't even using apt-get after a started my computer. this happens everyday since upgrading to 10.10 from 10.04 (32bit only). 100% on 1 core crap!!

---

### Post by earthpigg on 2011-04-11
theory:

update manager uses apt-get as its back-end.

start its GUI and take a look at how often it is set to check for updates?

---

### Post by HaRabAS on 2011-04-11
> **earthpigg said:**
> theory:

update manager uses apt-get as its back-end.

start its GUI and take a look at how often it is set to check for updates?

i did start start update manager yesterday but it gives me that FAILED TO LOCK error during install of packages.

---

### Post by earthpigg on 2011-04-12
> **HaRabAS said:**
> i did start start update manager yesterday but it gives me that FAILED TO LOCK error during install of packages.

then apt-get (or, very unlikely but possible: something claiming to be apt-get) is running rampant by itself, as root. possibly stuck in a loop.

that's a problem.

im assuming none of the other package managers work, either? ubuntu software center and synaptic? what about 'sudo apt-get update'? if one of them works, then that is probably the one that is running.

failing that, run these two commands:

```
ls /etc/init | grep apt-get
ls /etc/init.d | grep apt-get
```

both of those commands should return nothing. if one returns something, then we have our culprit. 

anyone else reading this: the above is kind of me throwing spaghetti at the wall and seeing if it sticks. i have no idea what would cause apt-get to start at boot and run at 100% constantly.

---

### Post by HaRabAS on 2011-04-12
> **earthpigg said:**
> then apt-get (or, very unlikely but possible: something claiming to be apt-get) is running rampant by itself, as root. possibly stuck in a loop.

that's a problem.

im assuming none of the other package managers work, either? ubuntu software center and synaptic? what about 'sudo apt-get update'? if one of them works, then that is probably the one that is running.

failing that, run these two commands:

```
ls /etc/init | grep apt-get
ls /etc/init.d | grep apt-get
```both of those commands should return nothing. if one returns something, then we have our culprit. 

anyone else reading this: the above is kind of me throwing spaghetti at the wall and seeing if it sticks. i have no idea what would cause apt-get to start at boot and run at 100% constantly.

both codes did not return anything, but now i get this from update manager:

[IMG]http://i105.photobucket.com/albums/m226/harabas/ss34.png[/IMG]

i don't know why it's still asking for the live cd. i used update manager for 10.10. some missing repositories i guess...darn, can't get this done now, tis' my office computer btw and this problem is making my cheeks go RED!!

---

### Post by plucky on 2011-04-12
Open "Software Sources" and un-tick the CDrom as a Source and see  if that makes a difference.

Good Luck

p.s. Please think about uploading as an attachment as it is painful to download a large jpeg on a slow connection.

p.p.s. If you still get the lock problem,you can delete the lock file in ```
/var/lib/apt/lists
```

---

### Post by HaRabAS on 2011-04-12
> **plucky said:**
> Open "Software Sources" and un-tick the CDrom as a Source and see  if that makes a difference.

Good Luck

p.s. Please think about uploading as an attachment as it is painful to download a large jpeg on a slow connection.

p.p.s. If you still get the lock problem,you can delete the lock file in ```
/var/lib/apt/lists
```

do i have to be root to delete that? coz i can't seem to delete it.

sorry for my questions, i'm a noob to the Linux world (basically it's everything about computers):Dblush:D

okay.

so i logged out from the current user.
chose sign as OTHER, type "admin" and then typed my Unix passwd, and bling, i can't log in as root.
i tried changing my password using the command "passwd" on the terminal and it says okay.

err...so much to do, but i like it, makes me feel like a PRO:lolflag:

---

### Post by plucky on 2011-04-12
> do i have to be root to delete that? coz i can't seem to delete it.


Ubuntu uses sudo as there is no Admin Account.

Open a terminal (Applications > Accessories > Terminal) and ```
sudo rm /var/lib/apt/lists/lock
```

It will ask for your password,but will not echo as you type the password.

Did you un-tick the CDrom in Software Sources?

---

### Post by antaios256 on 2011-04-12
> **HaRabAS said:**
> look at this:



and i wasn't even using apt-get after a started my computer. this happens everyday since upgrading to 10.10 from 10.04 (32bit only). 100% on 1 core crap!!

i had the same issue. go to update manager --> settings -->ubuntu software tab and make sure the cdrom option is unchecked 

leaving this option checked will result in apt-get doing its auto updates and freezing waiting for user input but not giving you a method of inputing the data.

---

### Post by HaRabAS on 2011-04-13
yep, i've "unchecked" the CD-ROM option on Update Manager/Synaptic.

now it's running fine. no more fuss with my Draftsight, Gimp and browser.

i'm also turning off "contain" plug-in from firefox as it's making me lag too.

thanks!!:D

---

