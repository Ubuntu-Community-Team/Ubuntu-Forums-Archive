---
title: "Ubuntu 10.04 won't recognize 1920x1080 resolution!"
date: 2010-09-09
forum: General Help
---

### Post by bronner on 2010-09-09
Hi, I have a serious problem: I just installed Ubuntu 10.04 on my computer which has a Hanspree HF257 25-inch monitor with a native resolution of 1920×1080. I have an NVIDIA GeForce 9400GT graphics card, and before I installed the proprietary NVIDIA drivers, the screen resolution was fine, but after I installed the recommended drivers, the screen resolution went way down after restart!

The monitor is recognized only as a &#8220;CRT-1 (CRT-1 on GPU-0)&#8243; under the NVIDIA X-Server settings. The highest resolution I can adjust it to is 1360×768. I have no idea what to do, but I'm sure there's a fix for this, right? Can someone please help me? It's kind of irritating.

---

### Post by bronner on 2010-09-10
Nobody has any solutions...?

---

### Post by tekkidd on 2010-09-10
Try installing the drivers from the nVidia website (or if you installed those than try the ones from the repo)

You may also want to go to the nvidia site and download an older driver (such as 180.xx) and see if the downgrade fixes the issue

---

### Post by bronner on 2010-09-10
> **tekkidd said:**
> Try installing the drivers from the nVidia website (or if you installed those than try the ones from the repo)

You may also want to go to the nvidia site and download an older driver (such as 180.xx) and see if the downgrade fixes the issue

Do they have the drivers for Ubuntu on the official website?

---

### Post by bronner on 2010-09-10
Okay, I downloaded a .run file from NVIDIA's website, and when I double click it, it says this:

Could not open the file /home/corey/Downloads/NVIDIA-Linux-x86-256.53.run.

gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again.

---

### Post by ubulal on 2010-09-10
You should really stay with the Ubuntu supplied Nvidia drivers, as parts of the package you downloaded from Nvidia.com *will* get overwritten by Ubuntu updates in the future possibly resulting in a broken system with no graphical desktop.

Anyway, to run that downloaded file: open a terminal and enter the following command:
```

sudo sh /home/corey/Downloads/NVIDIA-Linux-x86-256.53.run

```

---

### Post by bronner on 2010-09-10
I did and it gave me this message in a gray terminal:

You appear to be running an X server; please exit X before installing.  For further details, please see the section INSTALLING THE NVIDIA DRIVER in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).

---

### Post by ubulal on 2010-09-10
BTW, don't know how to fix your problem in the cleanest way.  I'd try moving /etc/X11/xorg.conf somewhere else and reboot, because modern X servers are said to detect almost everything automatically...

---

### Post by ubulal on 2010-09-10
> **bronner said:**
> I did and it gave me this message in a gray terminal:

You appear to be running an X server; please exit X before installing.  For further details, please see the section INSTALLING THE NVIDIA DRIVER in the README available on the Linux driver download page at [www.nvidia.com]("http://www.nvidia.com").

Press Ctl-Alt-F1 until you see a text mode screen.  Login with your username/password and enter

```

sudo /etc/init.d/gdm stop

```

and after that the command above.

---

### Post by bronner on 2010-09-10
> **ubulal said:**
> BTW, don't know how to fix your problem in the cleanest way.  I'd try moving /etc/X11/xorg.conf somewhere else and reboot, because modern X servers are said to detect almost everything automatically...

I really don't know how to do that, I'm sort of lost.

---

### Post by ubulal on 2010-09-10
> **bronner said:**
> I really don't know how to do that, I'm sort of lost.

```
sudo mv /etc/X11/xorg.conf /root
```and reboot.  If that should be even worse than before, do the opposite:

```
sudo mv /root/xorg.conf /etc/X11
```

---

### Post by bronner on 2010-09-10
> **ubulal said:**
> ```
sudo mv /etc/X11/xorg.conf /root
```and reboot.  If that should be even worse than before, do the opposite:

```
sudo mv /root/xorg.conf /etc/X11
```

Okay, so should I do that first command, reboot, then install the driver from the restricted hardware section?

---

### Post by ubulal on 2010-09-10
I thought you already have installed the Ubuntu-supplied Nvidia driver?  It must be installed first.  Then move /etc/X11/xorg.conf to /root and reboot.  If that doesn't work, move /root/xorg.conf back to /etc/X11 and continue looking for a solution ;)

---

### Post by bronner on 2010-09-10
Alright, that's what I'm trying now.

---

### Post by bronner on 2010-09-10
Alright, now when I open the NVIDIA XServer settings it gives me this:

You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

How do I run that as root?

EDIT:

I ran it as root and it gave me this:

corey@phoenix:~$ sudo nvidia-xconfig
[sudo] password for corey: 

WARNING: Unable to locate/open X configuration file.

New X configuration file written to '/etc/X11/xorg.conf'

corey@phoenix:~$ sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

corey@phoenix:~$ ^C
corey@phoenix:~$

---

### Post by ubulal on 2010-09-10
Looks good so far.  How about the resolution?

---

### Post by bronner on 2010-09-10
I reverted it back, because when I had the driver activated, it refused to even let me touch the resolution, the only two available were 800x600 and 640x480-- which is a disgrace both to my video-card and my monitor. :(

---

### Post by ubulal on 2010-09-10
"Detect Displays" button in Nvidia X Server Settings doesn't help?  No more ideas..

---

### Post by bronner on 2010-09-10
> **ubulal said:**
> "Detect Displays" button in Nvidia X Server Settings doesn't help?  No more ideas..

No, after following your instructions I couldn't even use NVIDIA X Server Settings. Oh well, thanks anyway.

---

### Post by ubulal on 2010-09-10
But now you can use nvidia settings again?  If not I'd be very sorry :(

---

### Post by bronner on 2010-09-11
> **ubulal said:**
> But now you can use nvidia settings again?  If not I'd be very sorry :(

No, I can't install NVIDIA without it messing up the screen resolution, and without it installed, my screen res is normal, but I can't use any of the rocking graphical effects. I don't know, I guess I'll just have to be patient with it, because it seems like they're not going to fix this problem for awhile, if at all.

---

