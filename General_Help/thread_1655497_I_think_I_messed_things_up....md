---
title: "I think I messed things up..."
date: 2010-12-29
forum: General Help
---

### Post by Mooseeeeey on 2010-12-29
Hey guys.  I'm new to Linux/Ubuntu, and have my hourly problem.  I was trying to get my Gfx Card driver installed, went through proccess, and it says I have X server(or something like that) running and that I need to remove it.  I went into software center and removed all the things with X server in the name, and rebooted.  Now the computer is stuck at Ubuntu splash screen with all the red dots on and not moving.  Is there a way I can restore whatever I did wrong through LiveCD or other means?

---

### Post by Mooseeeeey on 2010-12-29
Bump- Please help :(

---

### Post by oldos2er on 2010-12-29
Which video card do you have?

---

### Post by Mooseeeeey on 2010-12-29
Nvidia Geforce MX4000

---

### Post by Mooseeeeey on 2010-12-29
Nvidia Geforce MX4000

---

### Post by wojox on 2010-12-29
Can you get into recovery-mode or single-user-mode?

Try holding down the left shift key after reboot.

Then run

```
sudo apt-get update; sudo apt-get install --reinstall ubuntu-desktop
```

---

### Post by Mooseeeeey on 2010-12-29
When I get to GRUB2 I can choose recovery but don't know what to do there. Trying the code now.. Will report in a minute

---

### Post by Mooseeeeey on 2010-12-29
Nope, didn't work :/ still same splash screen with all red dots

---

### Post by Mooseeeeey on 2010-12-29
bump

---

### Post by Mooseeeeey on 2010-12-29
Bump.... Please :(

---

### Post by oldos2er on 2010-12-29
I would be careful bumping your post more than once in 24 hrs.

If you really removed all xserver-xorg packages, while in recovery mode run **sudo apt-get install xserver-xorg-video-nv** and see if that at least gets you to a desktop GUI.

---

### Post by thebarisaxkid on 2010-12-29
You said you deleted the X Server?  Yeah, that's kind of a bad thing...

I have no idea why it would need to be removed.  Maybe it needed to be restarted, but definitely not removed.  Hopefully you still have your install disc (or hopefully you can make another one)  because at this point, it would be hard to get X back up.  Reinstall Ubuntu and when you install your gpu driver, give exactly what it says, copy and paste, or better yet, a screenshot.  Maybe then we could be of more help.

---

### Post by Mooseeeeey on 2010-12-29
Sorry for the many bumps I guess I'm just really worried/ anxious/excited.  I have WoW updating now on my Windows drive, and will try you're code.  I think that was what I was looking for mainly was the name of the apt-get thing to install.

---

### Post by Mooseeeeey on 2010-12-29
Ok I tried what oldos2er said, and it didn't work.  Any more suggestions?

---

### Post by Idefix82 on 2010-12-30
"Didn't work" is not exactly the most detailed description of what happened that I can imagine. The only sensible answer to "didn't work" that I can think of is "try again". How about some more details?

Oh, and bumping every hour is akin to spamming.

---

### Post by Mooseeeeey on 2010-12-30
Well after I entered the code it went through with no errors, but after rebooting I still was stuck at splash screen with all 5 red dots.

---

### Post by oldos2er on 2010-12-30
Did you have a working desktop prior to uninstalling X? I think some legacy Nvidia support was dropped in 10.10, but I don't know the details.

---

### Post by Mooseeeeey on 2010-12-30
Yes, I had working Desktop and everything working as it should until I uninstalled Xserver.  At this point I'm wondering: Is there a way of only reinstalling / without messing with the things I have in /home?

EDIT: I just Google'd 'How to reinstall Ubuntu' and I cam across this command.  Does it look like it should work? It says it "reinstalls all the distribution packages and reconfigures them automatically."

```
sudo dpkg-reconfigure -phigh -a
```

---

### Post by oldos2er on 2010-12-30
It wouldn't hurt to try. Also **sudo dpkg-reconfigure xserver-xorg -phigh**

Is your /home on a separate partition from / ?

---

### Post by Mooseeeeey on 2010-12-30
I'm 99% sure it's a different partition.  During setup on LiveCD I made 3 partitons in my extended partion, and mounted them properly. Also, when I go on Windows, I see the 3 different partitions.  I'm going to try the 2 commands now and see what happens.

---

### Post by oldos2er on 2010-12-30
If you reinstall, and mount your current /home partition as "new" /home, make sure the box in front of format is *not* ticked. This way you preserve all your configuration preferences, as well as any other data you might want to keep.

And just FYI, dpkg-reconfigure only works on installed packages.

---

### Post by Mooseeeeey on 2010-12-30
OK: so with first command I got an error:
```
Since the script you are attempting to invoke has been converted to and upstart job, you may also use the reload(8) utility, eg. reload udev update-initramfs: Generating /boot/initrd.img-2.6.35-24-generic
Updating certificate in /etc/ssl/certs... 0 added, 0 removed; done.
Running hooks in etc/ca-certificates/update.d ....done.
update-initramfs:generating /boot/initrd.img-2.6.35-24-generic
cron stop/waiting
dpkg-maintscript-helper: error: couldn't identify the package

```
And when I tried the code you gave me it simply entered but didn't output anything into the console


Apparently, neither worked and I still have the issue.

With the suggestion of reinstalling, I still *mount* them, but I just don't use the "Format this drive" option?

EDIT: Reinstalled and working now, I believe it kept my home folder as I see my desktop background I set.  Reinstalling the few apps I installed.  Now to find the proper way of getting my graphics card driver in...

---

### Post by Yellow Pasque on 2010-12-30
Where did the Nvidia driver install tell you to remove X? Read error messages more carefully. As for installing the driver, enable the proposed repo and follow the directions for Selective Upgrading: [https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed) as it contains a version of the nvidia legacy driver that supports Maverick. DO NOT install other updates from proposed (unless you really want to).

Oh, and for future reference (should you need to install the nvidia driver manually), press Ctrl+Alt+F1, log in, and:
```
sudo service gdm stop
```

Then run the Nvidia installer.

---

### Post by Mooseeeeey on 2010-12-31
```
  ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at www.nvidia.com.

```
Is the error I get.  I don't know how to exit it. How do you?

EDIT: did as you said, went through first 3 or 4 steps and it said it couldn't install because of a Novuea (forgot spelling) driver error.  Now I rebooted because I didn't know how to get out of the Alt+Ctrl+F1, and my resolution is weird.  I tried to enter the mode ageain and typed
```
sudo service dgm start
```
and it said it was already running.
What do I now?

---

