---
title: "Can't Login"
date: 2009-12-11
forum: General Help
---

### Post by Timper on 2009-12-11
I have Ubuntu 9.10 first of all, so you don't need to ask which version I have. Yesterday my computer wasn't recognizing my USB flash drive after a system update so I restarted it. When it turned back on it loaded up normally but was a bit slow. After typing in my password and pressing login the computer shows the normal login animation thing but it goes on for about 30 seconds before opening Terminal in the upper left corner of the screen. I can enter commands in Terminal but they don't seem to do anything.

---

### Post by mcdjork on 2009-12-11
Run 'fsck' to see if it repairs your drive.

---

### Post by Timper on 2009-12-13
When I run "fsck" it says I do not have root access to the drive.  Is there any way for me to hook my computer up to another and transfer the files without the login working.  I have a couple essays on there I would really hate to retype.

---

### Post by Vinomfire on 2009-12-13
[SIZE="5"]Did you try doing 

sudo su
fsck[/SIZE]

---

### Post by Timper on 2009-12-13
I did do "sudo fsck"...it actually got a response but nothing seems to have happened, here is what it said:
 
*fsck from util-lunix-ng 2.16*
*e2fsck 1.41.9 (22-Aug-2009)*
*/dev/sda1 is mounted.*
 
*WARNING!!! Running e2fsck on a mounted filesystem may cause SEVERE filesystem damage.*
 
Do you really want to continue(y/n)?
 
 
After i said yes it came up with:
 
*/dev/sda1: recovering journal*
*/dev/sda1: clean, 221344/351468 files, 7242622/14044818 blocks*

---

### Post by happyhamster on 2009-12-13
Are you perhaps running an xterm session? When reaching the graphical login screen, click your user name. At the bottom of the screen, a few options should appera. Go to the Sessions option and choose "GNOME" and continue with the login.

If that doesn't work, boot into your "terminal" session, and type this into the terminal:

sudo touch /forcefsck && sudo shutdown -r now

It will cause a reboot and force a diskcheck. Good luck.

---

### Post by happyhamster on 2009-12-13
> **Timper said:**
>  
*WARNING!!! Running e2fsck on a mounted filesystem may cause SEVERE filesystem damage.*

This warning means what it says: you should not do this. It could really bork your drive (make it unbootable or cause major data corruption). Safe way of running fsck is from a live cd for example: boot into a live-session from the cd, and run fsck on the unmounted hard-disk (all hard drives will be unmounted by default). Another way is forcing a diskcheck during the regular boot-procedure (the drive won't be mounted yet at that time).

---

### Post by Timper on 2009-12-13
No sessions options come up when i click on my username except for what language and what keyboard style.  After running the filesystem check it rebooted and after logging in it did the same as before...just opened up the terminal.  Is there a way for me to connect my computers together and transfer files?

---

### Post by happyhamster on 2009-12-13
It should be possible to connect to another pc and transfer files, yes, but I can't help you there I'm afraid.

- Another way to try: boot until the graphical login screen appears, and press ctrl-alt-F3. This will drop you into a console. Login (note that you won't see anything when typing your password). Next, stop gdm (gnome display manager):

sudo service gdm stop

- Next, start the graphical part:

startx

---

### Post by Timper on 2009-12-14
I have decided to use a Live CD to try and access my files.  I can't find anything that will let me browse my old filesystem however, will someone please tell me how to do that?

---

### Post by Timper on 2009-12-14
Can anyone tell me how to find my old files after using a Live CD please?

---

