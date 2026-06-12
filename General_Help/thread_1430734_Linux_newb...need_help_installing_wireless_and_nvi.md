---
title: "Linux newb...need help installing wireless and nvidia drivers"
date: 2010-03-15
forum: General Help
---

### Post by phase constant on 2010-03-15
Well just like the title says..

New to linux, just installed the newest version of Ubuntu.  Currently plugged in to the cat5 to get on the web.

I have an HP dv4 laptop with broadcom wireless built in and need to get it running, when I go to HP support all the drivers are for Windows.

I have the nvidia 9M series, downloaded the correct driver from nvidia, i just don't know how to install it. 

I checked system>administation>hardware drivers 

and its empty, it says no proprietary drivers in use.

Could someone help please, I need my laptop fully functional for school this week.

---

### Post by howefield on 2010-03-15
Have you updated your package lists ?

Open a terminal, (Applications > Accessories > Terminal) and type

```
sudo apt-get update
```

Enter your password when prompted, you won't see it being entered but it will be.

Then try System > Administration > Hardware drivers again once the update is complete.

---

### Post by phase constant on 2010-03-15
Thanks for the quick response. I just did that and it updated in terminal.  Went back to hardware drivers and its the same...nothing there.

Whoops... update manager is running now.  5 min left.

---

### Post by Helkaluin on 2010-03-15
If you have downloaded the NVIDIA driver from their website (which should be something like 'NVIDIA-Linux-[your architecture]-[driver version]-pkgx.run') then all you have to do to install it is:

1. Stop the X Server. Press ctrl-alt-f2 to get to tty2, then type:

```
sudo /etc/init.d/gdm stop
```

2. Then change the directory to where you downloaded the driver installation file. So if it's the default:

```
cd ~/Downloads/
```

3. Then to run the installation with root privileges:

```
sudo sh ./NVIDIA-Linux-etcetcetc
```

4. After the installation simply restart the X Server by:

```
sudo /etc/init.d/gdm start
```

---

### Post by howefield on 2010-03-15
OK, Let it finish and try Hardware Drivers again, if still nothing, reboot and try Hardware Drivers again and post back if needs be.

Any HP with Broadcom that I have had or looked at, were taken care of through jockey (Hardware Drivers) picking them up.

---

### Post by Helkaluin on 2010-03-15
One more note: If you're installing NVIDIA drivers from their website instead of from the built-in 'Hardware Drivers' then it'll display it's own NVIDIA splash when you start the X Server.

Could be quite annoying, to turn it off you need to add the 'NoLogo' flag under 'Device' in /etc/X11/xorg.conf See [http://wiki.archlinux.org/index.php/NVIDIA#Disabling_the_logo_on_startup](http://wiki.archlinux.org/index.php/NVIDIA#Disabling_the_logo_on_startup) for details.

---

### Post by phase constant on 2010-03-15
Ok I let it finish installing and restarted.  I was able to select broadcom and nvidia drivers from the "Hardware Drivers" utility.  My wireless works, and it seems like I have video drivers (web pages load smoother when scrolling, etc).

So I think I'm good to go?

Do I still need to follow Helkaluin's instructions?

I've read a few basic guides but is there a specific one you guys recommend or anything else I should know?

Thanks for all the help.

---

### Post by howefield on 2010-03-15
> **phase constant said:**
> My wireless works, and it seems like I have video drivers (web pages load smoother when scrolling, etc).

Lovely Jubbly. :)

> Do I still need to follow Helkaluin's instructions?

Only if you want to use the drivers you downloaded, but why risk a working system (at least until you have the time/experience to fix any issues that might arise)?

---

### Post by phase constant on 2010-03-15
I like your style sir.  Thanks for the help again! I'm sure I'll be back soon.

---

### Post by howefield on 2010-03-16
> **phase constant said:**
> I've read a few basic guides but is there a specific one you guys recommend or anything else I should know?

Meant to include this last time, there is a free pdf download of the *Ubuntu Pocket Guide and Reference* you might want to get.

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

---

