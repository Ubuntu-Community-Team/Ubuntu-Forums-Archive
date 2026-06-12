---
title: "(New User)Totally messed up my install in etc/fstab please help"
date: 2010-06-09
forum: General Help
---

### Post by Make Space for Science on 2010-06-09
Hi,

After originally trying to install an .exe with wine i found a forum post with a step-by-step guide of mounting the disc and installing it that way, I'm quite a new user and still learning the Terminal commands..

Ok so after i edited the etc/fstab file I restarted my machine.. However..

When it boots an error occurs and I've spent days trying to fix it, you guys are my only hope!

The error message says 

'An error occured while mounting'
Press S to skip mounting or M for manual Recovery

If i press S it takes me to the same screen but this time with;

The disk drive for /tmp is not ready yet or not present

Continue to wait, or press S to skip mounting or M for manual recovery

When at this second screen, nothing works, pressing either S or M does nothing.

If i press M on the first screen it does take me to a 'terminal looking' screen, i have tried to edit the etc/fstab from this screen but it says it cannot be displayed.

Please Help! I know I can do a fresh install but i dont want to lose everything :(

I have recently upgraded to 10.4

EDIT: The screen displayed after i press M states the following...

Root filesystem check failed
A maintenance shell will now be started.
CONTROL-D will terminate this shell and reboot the system.
Root@jonny:~#

---

### Post by arrange on 2010-06-09
Could you boot into a LiveCD or such, mount the Ubuntu partition and post the **/etc/fstab** file?

Or - and this might be even easier - post the output of [boot_info_script]("https://sourceforge.net/projects/bootinfoscript/"). (If you don't know how to run the script, [look here]("http://bootinfoscript.sourceforge.net/").)

---

### Post by Make Space for Science on 2010-06-10
Sorry, I dont really understand..

Wouldn't I have to download the program onto the machine with ubuntu installed? or maybe i have missed the point.

Is the other option to download 10.4  onto CD and use that to boot?

---

### Post by Peter09 on 2010-06-10
at the terminal can you try the following command
 
```
ls -alg /etc/fs*
```
 
see if there is a file there called fstab.

---

### Post by libssd on 2010-06-10
If you are still posting here, you must have access to a working computer of some sort. Using it, you should be able to download an installable version of Ubuntu, and create a boot device using either an optical drive or a USB flash drive (at least 2 gb).

After several tries, I have never been able to get Ubuntu 10.04 to work on my hardware; 9.10, on the other hand, works flawlessly. Latest is not necessarily greatest, and I suggest you try installing an earlier version of Ubuntu. 10.4 (Lucid Lynx appears to have somewhat of a Jekyll/Hyde personality; if it works, it works, but if it doesn't, it's a disaster.

---

