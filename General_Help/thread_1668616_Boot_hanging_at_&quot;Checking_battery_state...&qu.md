---
title: "Boot hanging at &quot;Checking battery state...&quot;"
date: 2011-01-16
forum: General Help
---

### Post by Siramau on 2011-01-16
Today when I went to boot up my computer, it hung at "Checking battery state...". I have never had any problems before this, and have been using 10.10 for several months. The only change I made that I can think of was installing the Wacom Control Panel. Help, please! I have no idea what to do, and really, really don't want to reinstall Ubuntu unless there's no other option. Thanks in advance.

---

### Post by Siramau on 2011-01-16
Update: I tried running sudo apt-get update, and got about 3 screens of error messages. I don't think anything successfully installed. No idea if this is helpful.

---

### Post by Siramau on 2011-01-16
How annoying is it to bump a post? Sorry, but I'm desperate. I was stupid and didn't back up my hard drive, now I have several very important files that are only on my computer.

---

### Post by Siramau on 2011-01-17
Okay, so better question. Does anyone know what could cause this?

I reinstalled Ubuntu into another partition, but I really would rather fix my broken system then have to reinstall and recustomize everything. If I can't do that, I would at least like to know what I did to cause this problem so it does not happen again.

---

### Post by manishmahabir on 2011-04-13
same happened with me!
installed wacom control panel in natty 11.04 from the ppa ppa:hughescih/ppa
opened wacom control panel > rebooted > laptop hangs at checkin battery status....[ok]

no idea how to solve it...can you help me?

---

### Post by crcosmos on 2012-06-08
> **manishmahabir said:**
> same happened with me!
installed wacom control panel in natty 11.04 from the ppa ppa:hughescih/ppa
opened wacom control panel > rebooted > laptop hangs at checkin battery status....[ok]

no idea how to solve it...can you help me?
use aptitude in place of apt .. but if you use it in 'text-mode' it may ask you for use 'apt-cdrom' GOOD!!! if you have Ubuntu install disc in place, even though it wont fully mount >>> I believe the main culprit for this problem is within:

Gnome-desktop
Xfce
Video drivers :: found in lib/10.4-32-4-10-43-8/kernel/drivers/video
Net drivers :: ................. .................../drivers/net
mime ( because of crash log in /var )
and xulrunner %&with desktop-utils in Gnome section of install-level . .

Trying to restore these things, once you have internet established, of couse is a step / / /
I refered to a couple of the hi-level responses to this thread topic and some people really
know what they're doing here. The network-state involves more than we think . . .
Uninstalling and installing also....
............

> 

---

### Post by kira.argunova on 2012-06-08
Had the same problem, I took the easy way and just upgraded to Precise :) Worked for me!
The problem is generally due to some mess up with the graphics driver.
Also checked the gtk apps website, it clearly states that wacom doesn't work with ubuntu 11.04

try removing wacom

sudo apt-get purge wacom-tools

---

