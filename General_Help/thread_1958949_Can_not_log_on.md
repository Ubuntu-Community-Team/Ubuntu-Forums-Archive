---
title: "Can not log on"
date: 2012-04-15
forum: General Help
---

### Post by Achel4Ever on 2012-04-15
Hi, 
I'm running kde Linux-3.0.0.17, everything was running fine until my pc was froozen. After I start new it didn't boot anymore (stuck after it wrote Battery checing...) I tried with systemrecovery to check the filesystem, no errors. I used fix dpkg after that it boots normally until I get the logon window. I type username and password, the screen turns black and after a short while I get again the logon window. If I choose logon in console I can logon and everything using the command line works fine. 
I'm not very familiar with Linux, or KDE zo I don't realy know how to find the problem, can somebody please help me out?

Thanks you
Robin

---

### Post by zero2xiii on 2012-04-15
Sounds like a graphics bug?

I have had this once due to a broken xorg config file. Are your system specs enough to run the graphical environment? In other words what are your computer specs, more specificaly the graphics card??

Did you install any graphics drivers?

CHerz

---

### Post by Achel4Ever on 2012-04-15
Thanks for the reply. 
The system is more than a half year running without any problem concerning graphics whatsoever(also with quite heavy graphical demands). I didn't install or change anything. It might be the xorg config, since I suppose some file is corrupted what causes the trouble. How to check if it is ok?

I would like to analyze some Log-files, but there are so many, and I don't really understand how to read which one...

---

### Post by zero2xiii on 2012-04-16
Hmmm,

It is going to be somewhat tricky getting the informatation we require.

The config file is at: /etc/X11/xorg.conf

to view the file try:
```
cat /etc/X11/xorg.conf
```

If you are able to copy to a windows partition or usb drive, try something such as:

cat /etc/X11/xorg.conf > /path/to/windows/drive/xorg.txt
cat /etc/X11/xorg.conf > /path/to/usbdrive/xorg.txt

and then pasting the content here.

Also concerning the log files. The exact same method can be used. Log files that might be useful include:
/var/log/boot
/var/log/auth.log
**/var/log/xorg.0.log**   Most importent if this is a gui issue

If we can get the xorg.conf and the /var/log/xorg.0.log log we should be able to see whats going on if it is xorg related.

Cherz

---

### Post by Achel4Ever on 2012-04-16
I opened the xorg.conf file. Looks little weird to me (kind of empty) here is the result of cat /etc/xorg.conf

```

Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection

```The boot file is empty. The boot.log file has an interesting entry... You might be right in your first post saying it might have something to do with the graphical environment. 

The authentication log for today looks like:

```

Apr 17 08:25:27 Laptop kdm: :0[1744]: pam_unix(kdm:session): session opened for user robin by (uid=0)
Apr 17 08:25:27 Laptop kdm: :0[1744]: pam_ck_connector(kdm:session): nox11 mode, ignoring PAM_TTY :0
Apr 17 08:26:41 Laptop kdm: :0[1744]: pam_unix(kdm:session): session closed for user robin
Apr 17 08:35:59 Laptop kdm: :0[1506]: pam_unix(kdm:session): session opened for user robin by (uid=0)
Apr 17 08:35:59 Laptop kdm: :0[1506]: pam_ck_connector(kdm:session): nox11 mode, ignoring PAM_TTY :0
Apr 17 08:37:15 Laptop kdm: :0[1506]: pam_unix(kdm:session): session closed for user robin

```

The Xorg.0.log file, sorry, I don't understand any line of it... 

I hope this information helps you.

---

### Post by zero2xiii on 2012-04-17
Hay,

Yes it defenitly looks like a graphics bug. Just to make sure, right before you actualy log in, look around the screen, there should be a section you can select to log in type, or session type (Something like KDE should be the default one) Try selecting failsafe graphics or something similar, not the xTerm session (which only boots to a terminal, we can try this later)

After you have selected the fail safe graphics option, continue login in, if it is a minor graphics issue, this should resolve it temporarily and allow for a graphical environment for further debug.

If this fails completely, boot into xterm and try to start your xserver from there:

```
startx
```

this should give you warnings/error more specific to what happend right before the graphics crash. I have a strong feeling it is due to the nouveau driver error noted here:

```
[    79.002] (II) LoadModule: "nouveau"
[    79.003] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    79.003] (II) Module nouveau: vendor="X.Org Foundation"
[    79.003] 	compiled for 1.10.1, module version = 0.0.16
[    79.003] 	Module class: X.Org Video Driver
[    79.003] 	ABI class: X.Org Video Driver, version 10.0
[B][    79.003] (II) LoadModule: "nv"
[    79.003] (WW) Warning, couldn't open module nv
[    79.003] (II) UnloadModule: "nv"
[    79.003] (II) Unloading nv
[    79.003] (EE) Failed to load module "nv" (module does not exist, 0)[/B]
```

But this might be a secondary issue.

So first check if the fail safe graphics mode works, if it does, we can continue from there.

Cherz

---

### Post by Achel4Ever on 2012-04-18
Hello,

I found KDE failsave (no graphics failsave or whatever) but selecting it doesn't make any difference. 

Then I tried startx, and I got an error message Failed to load "nv" (module does not exist: 0)

I don't know how to make a screenshot in commandline, so I made a photo of the whole output, and uploaded it. 

I searched the internet little and I should get rid of the "nv", but since my xorg.conf is nearly empty I have no Idea where it gets it information which drivers to load. 
I tried xorg -create, and used this file to boot, but also no succes, then it complains that nvidia driver can not be loaded. I'm really not enough in this whole Xorg thing to find the problem myself, so realy appreciate your help!

Robin

---

### Post by HiImTye on 2012-04-18
try
```
sudo apt-get install nvidia-current
```
it should fix your problems

---

### Post by Achel4Ever on 2012-04-18
> **HiImTye said:**
> try
```
sudo apt-get install nvidia-current
```it should fix your problems

Unfortunately it didn't work. I get quite a lot of error messages during installation, but at the end it stated successfully installed. 

Trying to log in I get the same error as before. 

I also tried login after I removed the xorg.conf file completely, this seems to have no influence at all.

---

### Post by HiImTye on 2012-04-18
```
nvidia-xconfig
```
try this

---

### Post by zero2xiii on 2012-04-18
> **HiImTye said:**
> ```
nvidia-xconfig
```
try this

Needs sudo appended:

```
sudo nvidia-xconfig
```

Otherwise it usualy gives an auth error

Cherz

---

### Post by Achel4Ever on 2012-04-18
nvidia-xconfig worked. My graphics driver problem disappeared. 

On the other hand it made the problem actually bigger. 
After I ran it, I still can not log on to kde (exactly the same as before) but as far as I can see I also don't get any error anymore! 

I found still 1 entry in the boot.log, Stopping automatic crash report generation failed! But I have no idea if this could cause my trouble, not even to mention how to get rid of it.

I'm really getting desperate and start considering install the system new. But I would be very very unhappy to do so, since after long time finally had the system working how I like it, now this... But I still have a feeling it should be solvable. So I sincerely hope some of you have a good idea so we find the problem. Anyway thanks for your help already so far. 

Robin

---

### Post by zero2xiii on 2012-04-19
Hay,

Glad your graphics issue is resolved. However I am numbed by the issue you now have. No errors? Nothings seems to be wrong.

Try again what I said earlier with the safe graphical mode and terminal session and such. It might still be a graphical issue, just not being able to generate the error.

If its not, I have no idea how to continue any further, maybe some one with more experience can help you finding and fixing the persisting issue.

Cherz

---

### Post by Achel4Ever on 2012-04-20
So I found an error! 
I searched th net and tried about everything what other people did with similar problems but still can't get my sytem running.

Here is the content xsession.errors of the last time I tried to log in 

```

Xsession: X session started for robin at Fri Apr 20 11:31:30 CST 2012
Smart Common Input Method 1.4.9

Launching a SCIM daemon with Socket FrontEnd...
Loading simple Config module ...
Creating backend ...
Loading socket FrontEnd module ...
Starting SCIM as daemon ...
Launching a SCIM process with x11...
Loading socket Config module ...
Creating backend ...
Loading x11 FrontEnd module ...
GTK Panel of SCIM 1.4.9

Gtk-Message: Failed to load module "canberra-gtk-module"
Starting SCIM as daemon ...
SCIM has been successfully launched.
script for scim started.
script for auto started.
script for default started.
startkde: Starting up...
kdeinit4_wrapper: Warning: connect(/home/robin/.kde/socket-Laptop/kdeinit4__0) failed: : Connection refused
Bus error
startkde: Shutting down...
kdeinit4_wrapper: Warning: connect(/home/robin/.kde/socket-Laptop/kdeinit4__0) failed: : Connection refused
Error: Can not contact kdeinit4!
startkde: Running shutdown scripts...
startkde: Done.

```Can somebody please telll me what to do to get in my computer again. 
Or alternatively (since I start loosing my faith I will ever get this fixed) how to install new with loosing as few as possible of my old system. 

Thanks a lot.

---

### Post by zero2xiii on 2012-04-21
Hay,

I can try to help further but no promises.

First, you can just re-install over your current system and NOT FORMAT, to keep any user data such as files, videos, pictures and so forth in your home folder. However this MIGHT cause issues with configuration files if installed as the EXACT same username, for example if your current user is "Me" then make the new install "Me too" or similar.

As far as your issue is concerned, try the following from a fail safe terminal, or during boot select recovery console and then root shell at the very bottom. Or you can try using a TTY before login by hitting ctrl + alt + F1... 

Then do the following:

```
sudo apt-get purge kdm #sudo not needed if root shell, this purges your KDE window manager and all related config files
sudo apt-get update
sudo apt-get install kdm
```

This purges and reinstalls all the window manager related files and configs. If the error continues after the fresh install. Then I have no idea how to recover the system, except for installing another desktop environment such as Gnome or something else.

Just before you completely give up, a shot in the dark, try owning what is giving the issue:

```
sudo chown -R $(whoami) /home/robin/.kde/socket-Laptop
```

Please note this is a TOTAL shot in the dark, a very small rock into a GIANT bush. This might break the system so use caution. Only do this as a last resort!

Before you reinstall the system and risk loosing everything, you might want to install another desktop environment? I suggest Gnome, however you might want to go more lightweight if you just want to use it to back up your files.

```
sudo apt-get install gnome #this installs only gnome
sudo apt-get install ubuntu-desktop #this installs the FULL ubuntu desktop
```

Cherz and good luck

---

### Post by Achel4Ever on 2012-04-25
Just want to say thanks for you help! 
My problem didn't get solved, but hey, I learned a lot :) 

Ended up reinstalling my system (about 15 times), made a backup of my home directory first, and found out that recovering everything is a lot more easy then expected. Few days ago I was considering giving up, now I'm considering defenitly deleting my windows partition. 

Thanks again for your help!

---

### Post by zero2xiii on 2012-04-26
Hay,

Glad you got some experience and a new excitement... Hahaha most people trying out ubuntu (or any linux) find it daunting at first... But if they are willing to just hold on a bit untill they get to know it.. They find it worth it most of the time :). 

But yea. Good luck with your further exploration, we are here to help each other out as best we can. (ubuntu does mean humanity after all - In zulu anyway.....)


Cherz

---

