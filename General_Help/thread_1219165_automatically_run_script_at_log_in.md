---
title: "automatically run script at log in"
date: 2009-07-21
forum: General Help
---

### Post by markymark1 on 2009-07-21
Hi,

I am a new user and am attempting to resolve a problem with the Elantech touchpad on my laptop.  Ubuntu 9.04 does not recognise the touchpad at login.  However, I have found the following script to address the problem:

sudo modprobe -r psmouse
sudo modprobe psmouse proto=imps

This works fine but is only good for that session.  Every time I reboot, I have to run the script again.  The difficulty here is that without the touchpad, I'm unable to open terminal in order to run this script.  Thus, I have to borrow someone else's USB mouse in order to open terminal and regain use of my touchpad.  This is frustrating and not a long term solution.

I have created a script file with the above script and inserted as the first line:

#!/bin/bash

I understand that I have to make the file executable, so I have also used the terminal to input the following:

sudo chmod +x /home/mark/elantech.sh (with the last bit being the file path)

I have then added this script file to the list of startup applications under system > preferences.  However, nothing happens at log in.  The script file seems to be OK.  If I use the USB mouse to double click on the script file and select 'run in terminal', I am prompted by the terminal to enter my password.  Having done that, I obtain use of the touchpad again.

Is anyone able to describe a means by which I can successfully automate this process at log in (or, at the very least, open up the terminal automatically at log in)?

Many thanks. 

Mark

---

### Post by bacil on 2009-07-21
wouldnt it be better to have it started on startup not at login ? say in rc3 ?

so you should do something like this in /etc/rc3.d/

```
sudo ln -s /path/to/your/script.sh S99pcmouse
```

this will run your script every time your computer goes to runlevel 3 that is runlevel when network and all services are started

---

### Post by sisco311 on 2009-07-21
```
gksu gedit /etc/modprobe.d/psmouse.conf
```
add this line to the file:
```
options psmouse proto=imps
```
save the file and reboot.

---

### Post by bacil on 2009-07-21
sorry had second thought

you should check if module is loaded before you are loading it again so i would add that to your script, it should look like this on the end

[PHP]#!/bin/bash

MODULEE=`lsmod | grep psmouse | wc -l`
if [ $MODULEE -ne 0 ]; then
  echo "Module already loaded"
  exit 1
else
  echo "Loading module"
  sudo modprobe -r psmouse
  sudo modprobe psmouse proto=imps
fi[/PHP]

and you should make it executable as you say in your post

---

### Post by markymark1 on 2009-07-21
Thank you Sisco311.  That has done the trick.  I'm very grateful.

Thank you also Bacil for taking the time to offer a solution.

Mark

---

### Post by sisco311 on 2009-07-21
Cool!

btw, Welcome to the forums!

---

### Post by mikey_likesit on 2009-07-25
> **bacil said:**
> sorry had second thought

you should check if module is loaded before you are loading it again so i would add that to your script, it should look like this on the end

[php]#!/bin/bash

MODULEE=`lsmod | grep psmouse | wc -l`
if [ $MODULEE -ne 0 ]; then
  echo "Module already loaded"
  exit 1
else
  echo "Loading module"
  sudo modprobe -r psmouse
  sudo modprobe psmouse proto=imps
fi[/php]and you should make it executable as you say in your post


i'm having something of a similar problem, been discussing in another post ([http://ubuntuforums.org/showthread.php?t=1221371](http://ubuntuforums.org/showthread.php?t=1221371))

I wonder if running a script at startup (level 3? 6?) would allow me to assign an ip to eth0 and automount a couple of network drives? I tried making a link to my script (pasted below) in /etc/rc3.d (tried rc6.d as well, just to see), renaming the file to S99networkmount, but couldn't get it to work.

```

#!/bin/bash

gksudo ifconfig eth0 169.254.9.9
gksudo smbmount //169.254.157.241/disk /mnt/networkdisk
gksudo smbmount //169.254.157.241/usbdisk2 /mnt/networkdisk2
```Any ideas where I've gone wrong? Is what I'm trying to do *** backward? I've tried doing this in /etc/fstab but couldn't get it to work there either. When I run the script through System>Preferences>Startup it works, but I get a password prompt every time, which is kind of annoying.

---

