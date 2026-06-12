---
title: "Add Startup Script To Live Linux Distro"
date: 2012-01-05
forum: General Help
---

### Post by planetofdeviants on 2012-01-05
I want a live Linux distro that is customised to have only one change:  a python script that launches when it starts up.

I have two basic areas to understand to solve this problem:  (1) Make a script that lauch unix commands as well as programs like firefox, gedit, etc.  (2)  Add the script to a live distro.

Anyone know how to do this?  


**Steps To Add Startup Script to Live Linux Distro**

No steps now.  (need help with these steps)


**Steps to Make Startup Script**

[I]problems to be solved:
(1)  the following solution requires and update and boot (step 4).  Can't do that with live distro only installed distro.
 (2)  this script won't launch programs like gedit or firefox, only commands like ls, mkdir, mount, etc.[/I]
 [I]
 Note:  I have to use python, instead of Bash, because later on I will be adding more python.[/I]

1.  Create a file containing this text (this is the python script):

```
#! /usr/bin/python

import os

unixCommand1 = "mkdir /home/ubuntu/test"
os.system(unixCommand1)

unixCommand2 = "firefox" # this won't launch firefox???
os.system(unixCommand2) 


```2.  Copy this script to the directory
```
 /etc/init.d
```3.  Create this link

```
sudo ln -s /etc/init.d/startup.py /etc/rc3.d
```4.  Run update

```
sudo update-rc.d startup.py defaults
```

---

### Post by Paddy Landau on 2012-01-06
I don't know Python, so I can't help you write the script (unless you are happy with a Bash script), but I can help you with placing your startup if you use Ubuntu.

The script in /etc/init.d is not a good place to put something like Firefox, because it will start in root before you are logged in!

What you want is a script that will start *after* you log in.


[LIST=1]
[*]Write your script, obviously saving it somewhere (for example /home/planetofdeviants/mystartupscript).
[*]Ensure that the file has the executable bit set.
[*]Run your script to ensure that it works.
[*]Open *Startup Applications*.
[*]Press *Add*.
[*]Type a descriptive name.
[*]For the command, enter the full path, e.g. /home/planetofdeviants/mystartupscript
[*]Write an explanatory comment.
[*]Press *Add*.
[/LIST]

Log out; log in; your script should run within seconds.

---

### Post by planetofdeviants on 2012-01-06
Okay, now I can start up gui stuff.  Thanks.

All I want to do now is add that script to a Live Ubuntu iso. 

Remaster and Relinux are lackig dependencies based on all the latest articals I've found.  So I haven't got remastering working yet.

Puppy linux has a super easy remaster, but it left out my start up scripts.  Would this happen in Ubuntu also if I found a remaster process that was up to date?

---

### Post by Basher101 on 2012-01-06
try Remastersys..it does a full backup of your current install with all changes (settings and installed programs) and makes a bootable live .iso

regards

---

### Post by planetofdeviants on 2012-01-06
Yes, but what Ubuntu version should I use to guarantee it works?

---

### Post by Basher101 on 2012-01-06
> **planetofdeviants said:**
> Yes, but what Ubuntu version should I use to guarantee it works?

the one that works with your pc right now obviously

---

### Post by Paddy Landau on 2012-01-07
There is an easier way.

Create a Live USB using the standard Ubuntu way (i.e. using Startup Disk Creator), choosing to have persistence. (You'll want a USB of at least 4Gb, which fortunately these days is pretty cheap.)

When you boot from the Live USB, it will remember any changes that you make.

---

