---
title: "How do you figure out what your kernal version and name is?"
date: 2006-04-14
forum: General Help
---

### Post by Dakaru on 2006-04-14
I want to run this command, but I don't know what my kernal is named, its a default Ubuntu Kernal fresh outa the box. 


Command Im trying to run for ati drivers.

vivi@Beta:~$ $ sudo apt-get install linux-restricted-modules- xorg-driver-fglrx

---

### Post by jbrader on 2006-04-14
Go to the terminal and enter:
uname -r

---

### Post by dermotti on 2006-04-14
uname -r

---

### Post by Dakaru on 2006-04-14
[QUOTE=jbrader]Go to the terminal and enter:
uname -r[/QUOTE]

Well, when I type the command in, I get the following.



sudo apt-get install linux-restricted-modules-2.6.12-9-386 xorg-driver-fglrx
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

Im trying to follow this guide.


________________________________
[http://www.ubuntuforums.org/showthread.php?t=24557](http://www.ubuntuforums.org/showthread.php?t=24557)

---

### Post by towsonu2003 on 2006-04-14
[QUOTE=Dakaru]
sudo apt-get install linux-restricted-modules-2.6.12-9-386 xorg-driver-fglrx
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory
[/quote]
make sure you do not have apt-get or synaptic running. close synaptic and check if apt-get is running (updating in the background) with
ps aux | grep apt
only line you're supposed to get is: 
yourusername   11235  0.0  0.0   3248   744 pts/2    R+   00:19   0:00 grep apt

if more than one lines, wait until apt-get exits...

---

### Post by oscar on 2006-04-14
you can also use the uname -r in the apt commands:
```
sudo apt-get install linux-restricted-modules-$(uname -r)- ...
```

---

