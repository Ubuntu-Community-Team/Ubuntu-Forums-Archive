---
title: "How do I get Owner Permissions?"
date: 2010-11-12
forum: General Help
---

### Post by SINNISTER on 2010-11-12
Hey all

I am trying to change the write permissions on a file and On the screenshot you will see where i have underlined, its states i dont have owner rights to modify this file, how do I get owner Permissions when this is my installation....

[IMG]http://img530.imageshack.us/img530/6959/screenshotvh.jpg[/IMG]

thanks a lot

---

### Post by WorMzy on 2010-11-12
That file is owned by root.

Change ownership with

```
sudo chown USERNAME:GROUP
```

Use at your own discretion. If that file needs to be owned by root, then changing it's ownership to your user may cause problems.

Read
```
man chown
``` for more information.

---

### Post by Skavenger0 on 2010-11-12
To Change owner use:

```
sudo chown user:group /filename
```

To change the Permissions for either the user group or others use:

```
sudo chmod ### /filename
```

Where ### is a 3 digit permission reference:

Each # refers to either Owner/Group/All

Read = 4
Write = 2
Execute = 1

Add the Necessary Numbers together to get your code so:
775 =
Owner = rwx
Group = rwx
All = rx

---

### Post by Verbeck on 2010-11-12
sudo chmod xxx /path/to/file

see this man page for more info
[http://ss64.com/bash/chmod.html](http://ss64.com/bash/chmod.html)

edit : as someone already posted, changing the ownership may cause some problems

---

### Post by dFlyer on 2010-11-12
Before you go changing ownership of a file in linux make sure you know what you are doing. Since you asked the question, I don't think you're sure what your doing. If you want to configure this file please follow below link:

Installing and Configuring Lampp (the simple guide) — Alan Edwardes
Oct 24, 2007 ... I've decided to create this post in the hope that anyone else trying to configure lampp on Ubuntu Linux doesn't have to look in completely ...
[www.alanedwardes.com/.../installing-and-configuring-lampp-the-simple-guide/](www.alanedwardes.com/.../installing-and-configuring-lampp-the-simple-guide/) - United Kingdom - Cached

---

### Post by I'mGeorge on 2010-11-12
well the right commands were already posted but as a more straight forward way, just open your terminal, sudo nautilus (or the name of your usual file browser, in Gnome it's nautilus in Kde it's dolphin) followed by the password and in nautilus go and change the permission of any file you would like as now you can use your file manager with root privileges

---

### Post by Skavenger0 on 2010-11-12
On that note if you dont want to make the change perminant then just use sudo to get temporary access to the file.

---

### Post by WorMzy on 2010-11-12
> **I'mGeorge said:**
> well the right commands were already posted but as a more straight forward way, just open your terminal, sudo nautilus (or the name of your usual file browser, in Gnome it's nautilus in Kde it's dolphin) followed by the password and in nautilus go and change the permission of any file you would like as now you can use your file manager with root privileges

For graphical applications you should use **gksudo**, not sudo. Using sudo for graphical apps can cause problems with your .ICEauthority file, as well as any files in your home folder associated with the application.

---

### Post by SINNISTER on 2010-11-12
Hey 

thanks guys.

But the last time i used "nautilus" it completely messed up my permissions and i could not even save a file to my desktop. so i have no clue in what route to take please can you advise the simplest way that it does not effect all the other permissions.

thanks again thou :)

---

### Post by AlphaLexman on 2010-11-12
pcmanfm:
```
sudo apt-get install pcmanfm
```is a lightweight GUI file manager that handles permissions in an easy to understand method.

Then,
```
 sudo pcmanfm
```Right click the file, click Properties -> Permissions

---

### Post by WorMzy on 2010-11-12
> **SINNISTER said:**
> Hey 

thanks guys.

But the last time i used "nautilus" it completely messed up my permissions and i could not even save a file to my desktop. so i have no clue in what route to take please can you advise the simplest way that it does not effect all the other permissions.

thanks again thou :)

The simplist method is to use chown/chgrp/chmod.

---

### Post by SINNISTER on 2010-11-13
THanks guys alright I'll proberly try "WorMzy"s way.

if this is the path to the file:

/home/server/Desktop/lampp

how would i do it?

thanks

---

### Post by kanishkdudeja on 2010-11-13
```
sudo chown -R username:groupname /home/server/Desktop/lamp
```

---

### Post by SINNISTER on 2010-11-13
Flipping finally, 

thanks guys :)

how do i make this thread as "SOLVED"

thanks again thou guys you have saved me once again :)

---

### Post by SINNISTER on 2010-11-13
:) :) :) :)

---

### Post by Verbeck on 2010-11-13
under thread tools at the top

---

