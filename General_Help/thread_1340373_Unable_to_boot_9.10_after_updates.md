---
title: "Unable to boot 9.10 after updates"
date: 2009-11-28
forum: General Help
---

### Post by DiscoStu570 on 2009-11-28
I've had ubuntu 9.10 running fairly uneventfully on my machine for a little less than a month now.  The install is on a relatively new 500gig seagate hard drive, which I have no reason to believe is faulty.

Now, before today, I've had no problems booting this machine.  Yesterday, a pretty big batch of updates were installed.  Today when I turn the machine on, I get a black screen with the silver ubuntu logo on it, and then usually the following error message for a moment below it:

One or more of the mounts listed in /etc/fstab cannot yet be mounted 
/:waiting for /dev/sda1/eed0aee7-e381-4ec9-a6df-d38e2f07d59c
/tmp waiting for (null)
Press escape to enter a recovery shell

Pressing escape has yet to change the following.  After a moment, I get a black terminal screen with the following 2 lines:

Ubuntu 9.10 patrick-desktop tty1

patrick-desktop login:

This screen is blinking rapidly, and the keyboard responds poorly enough that I'm unable to type in my password to log in and get any further.

---

### Post by RedSingularity on 2009-11-28
What happens when you type 

sudo /etc/init.d/gdm start

---

### Post by DiscoStu570 on 2009-11-28
I'm unable to get past the login to get to a command line to try that.  Basically, the keyboard is blinking in the same way that the screen is.  I can get my login in because I can see the characters to know when they have or haven't been entered, but the password doesn't display as you type it.

---

### Post by DiscoStu570 on 2009-11-28
I can load well enough off the ubuntu cd, and can access everything on the hard drive it says is slow to load, so it's not a hard disk problem.  Something in the updates scrambled me up somehow.

---

### Post by DiscoStu570 on 2009-11-28
Problem solved, its the same problem I frequently had in 9.04 when ubuntu updates came calling, but never caused quite the same symptoms.  I simply had to recompile my NVIDIA drivers.  I couldn't even begin to imagine why the computer reports a general error mounting the file system when in fact it's a video driver problem, but that appears to be the case.

For anybody seeing this thread and having the same problem, hold shift while the computer is loading up, and boot into recovery mode.  You'll need to acquire the latest ubuntu drivers, which NVIDIA makes available on their website.  Once they're on your computer enter a terminal, type /etc/init.d/gdm stop, change directories to the directory where the NVIDIA driver package is, and type:
sh NVIDIA* 
where NVIDIA* is the full name, with correct capitalization and such, of the drivers package.  In my case it's NVIDIA-Linux-x86-185.18.31.pkg1.run, but they update and rename the files from time to time, so make sure you get it right.  Then let the program run and reboot.

---

### Post by X1R1 on 2009-11-28
I got this same error...but completely different solution/sympthoms

My drive was running very slow and suddenly when I restarted it this message appeared, I run a hard disk test and found a bunch of errors, now everything works fine. For me this was a hard disk problem not video drivers.

---

