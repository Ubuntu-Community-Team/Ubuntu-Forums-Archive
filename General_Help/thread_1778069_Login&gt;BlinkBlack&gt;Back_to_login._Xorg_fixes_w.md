---
title: "Login&gt;BlinkBlack&gt;Back to login. Xorg fixes wont help."
date: 2011-06-08
forum: General Help
---

### Post by ==Troy== on 2011-06-08
Hello!

I am very lost as to how to fix the issue, and re-installing ubuntu is going to be quite a task (a lot of non-repo software)

Symptoms :
-Boot to login screen
-Enter password
-It proceeds with animation of the log-in prompt disappearing
-Blinks black + some text
-Last line of that some text is "ome directory /etc/timidity/ is not ours"  the "ome" is not a typo, it is exactly like that.
-Drops me back to the user choice.

-Happens to any user, even newly created


Attempted fixes:
- Tried a lot of suggested Xorg fixes in similar threads, all with no or worse results than initially
- Re-installed ubuntu on a new drive, and copied over the X11 folder entirely to the old install, with  no changes to the problem.
- Purged nvidia drivers and installed new ones, with no result
- Nothing is written into xorg log files.


System :

Ubuntu 10.04 LTS
Nvidia video card.


Additional notes :
On the day I had to switch between windows/linux quite a bit, and after about 6th restart, it gave some error about xorg (after login), I, as a matter of reflex, told it to restart X, and then it hang, so I had to hard-reset the computer. After this, the login issue started happening. 


Thank you in advance!

---

### Post by hal8000 on 2011-06-08
> **==Troy== said:**
> Hello!

I am very lost as to how to fix the issue, and re-installing ubuntu is going to be quite a task (a lot of non-repo software)

Symptoms :
-Boot to login screen
-Enter password
-It proceeds with animation of the log-in prompt disappearing
-Blinks black + some text
-Last line of that some text is "ome directory /etc/timidity/ is not ours"  the "ome" is not a typo, it is exactly like that.
-Drops me back to the user choice.

-Happens to any user, even newly created





Attempted fixes:
- Tried a lot of suggested Xorg fixes in similar threads, all with no or worse results than initially
- Re-installed ubuntu on a new drive, and copied over the X11 folder entirely to the old install, with  no changes to the problem.
- Purged nvidia drivers and installed new ones, with no result
- Nothing is written into xorg log files.


System :

Ubuntu 10.04 LTS
Nvidia video card.


Additional notes :
On the day I had to switch between windows/linux quite a bit, and after about 6th restart, it gave some error about xorg (after login), I, as a matter of reflex, told it to restart X, and then it hang, so I had to hard-reset the computer. After this, the login issue started happening. 


Thank you in advance!


I have 10.04 on my laptop. Ubuntu 10.04 does not use Xorg I dont even have an /etc/X11/xorg.conf. kernel mode settings are used to setup X and resolution.
At the login screen, can you login at an alternate console?
Try ctrl+alt+F2

login with username and password then type:
startx

This may give a more detailed error.
As the error mentions timidity, you may be able to remove timidity:
sudo apt-get remove timidity

but try the alternate console first

---

### Post by ==Troy== on 2011-06-08
Ok, after getting into tty2 and doing startx I get this :


xauth:  /home/username/.Xauthority not writable changes will be ignored
xauth: error in locking authority file /home/username/.Xauthority
//repeated 2x




Fatal server error :
Server already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again


Please consult ..... for help

ddxSigGiveUp: Closing log
No protocol specified giving up.
xinit : Resource temoprary unavailable errno11 unable to connect to X server
xinit: no such process errno3 server error
xauth : error in locking authority file /home/username/.Xauthority

---

### Post by nerdy_kid on 2011-06-08
run:

```

sudo rm ~/.Xauthority
sudo reboot

```


See if that fixes it.  .Xauthority permission errors are caused by running GUI apps with the sudo command, for example sudo nautilus.  DO NOT run gui apps with sudo, use gksu instead -- e.g. gksu nautilus.

---

### Post by ==Troy== on 2011-06-08
Allright, after removing the Xauthority, rebooting, I still get the same issue.

When I get back to tty2 and startx:

twice:
xauth: creatinng new authority file /home/username/.Xauthority


Fatal server error 
Server is already active for display 0
....

....

....
ddxSigGiveUp : Closing log
invalid MIT-MAGIC-COOKIE 1 keygiving up
xinit : same errno11 and errno3

---

### Post by SavageWolf on 2011-06-08
On tty2, could you run "ls -la /etc/timidity/"?

Also, have you tried an earlier kernel?

Also, try "sudo adduser test", and logging in as test.

---

### Post by nerdy_kid on 2011-06-08
post your gdm logs please:

```

gksu gedit /var/log/gdm/:0.log

```

---

### Post by ==Troy== on 2011-06-08
Realise I dont have any GUI :P

ended up getting nano to  check that log,

the relevant part I assume (the log is big)
...
....
VESA: driver for VESA...
FBDEVL driver for....
(EE) [drm] failed to open device
(WW) Falling back to old probe method for fbdev
loading /usr/lib/xorg/modules/linux/libfbdevhw.so
.....


(==) RandR enab;ed
(EE) Failed to initialise GLX extension (Compatible Nvidia X driver not found)
XKB: reuse xkmfile /var....

...
...

no input driver/identifier specified (ignoring) // possibly this is related to my joystick?

---

### Post by nerdy_kid on 2011-06-08
> **==Troy== said:**
> Realise I dont have any GUI :P

ended up getting nano to  check that log,



lol, sorry about that :oops:

try:

```

sudo nvidia-xconfig
sudo service gdm restart

```

---

### Post by ==Troy== on 2011-06-08
Nope, that didnt do anything about the problem.

Now though I have Nvidia logo blink for every black-gui or gui-black switch.

I have also tried purging nvidia drivers and re-installing htem with no success.

---

### Post by nerdy_kid on 2011-06-08
> **==Troy== said:**
> Nope, that didnt do anything about the problem.

Now though I have Nvidia logo blink for every black-gui or gui-black switch.

I have also tried purging nvidia drivers and re-installing htem with no success.

are the logs any different?  Check /var/log/Xorg.0.log as well.

can you please do

```

lsmod

```

---

### Post by nerdy_kid on 2011-06-11
try

```

sudo update-initramfs -u

```

and reboot.

---

