---
title: "Ubuntu 11.04 Server  minimal gnome"
date: 2012-04-07
forum: General Help
---

### Post by logman on 2012-04-07
Hi,

Is there anyway to install ubuntu server 64bit, minimal gnome classic gui?

I don't want lose server kernels. 


What i did try 

```
sudo apt-get install --no-install-recommends ubuntu-desktop
```in terminal when i run: "startx"     i only get desktop, nothing else.

---

### Post by jerrrys on 2012-04-07
That should of worked.  You should boot straight to desktop.  Getting any errors?

---

### Post by logman on 2012-04-07
> **jerrrys said:**
> That should of worked.  You should boot straight to desktop.  Getting any errors?

I only see desktop, no menus etc.

Here is link to desktop.   [[COLOR=Red]**LINK**[/COLOR]]("http://logman.miumau.net/ubuntu/ubuntu_tyopoyta.jpg")

---

### Post by jerrrys on 2012-04-08
This is 11.04.  try:

sudo service gdm restart

Also ran across this

[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)

Is there a reason for 11.04?  11.10 is already out and 12.04 will be out later this month.

Also as of 12.04 the server (PAE) kernel is default kernel for desktop installs.

---

### Post by logman on 2012-04-08
> **jerrrys said:**
> This is 11.04.  try:

sudo service gdm restart

Also ran across this

[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)

Is there a reason for 11.04?  11.10 is already out and 12.04 will be out later this month.

Also as of 12.04 the server (PAE) kernel is default kernel for desktop installs.

I did remember wrong  i have 11.10.

Okay i got unity running, trying to change to Classic mode, can't really open gnome-terminal box.

But thanks that i got more than desktop showing up. !  :)

---

