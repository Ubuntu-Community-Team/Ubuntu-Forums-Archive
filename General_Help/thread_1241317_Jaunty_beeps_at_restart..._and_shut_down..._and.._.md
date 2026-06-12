---
title: "Jaunty beeps at restart... and shut down... and.. finally made it stop!"
date: 2009-08-15
forum: General Help
---

### Post by centaurusa on 2009-08-15
...but, only by using an inelegant kludge. 
 
higashi ([http://ubuntuforums.org/showthread.php?t=1139234](http://ubuntuforums.org/showthread.php?t=1139234)) and a number of other Ubuntu 9.10 users have threads basically complaining about the loud beep that accompanies a system shutdown or restart on many machines.  I had the same problem on a Dell Inspiron 6400 laptop.  

Fortunately, the advice to unload the PC speaker module with the command (without quotes) "sudo modprobe -r pcspkr" works on my machine.  But, as noted in the message threads this command only applies to the current session.  So, while the first shutdown or restart is (mercifully) quiet, the beep returns next time around.   

The second part of the usual advice is to "prevent the PC's speaker module from ever loading" by adding the line (without quotes) "blacklist pcspkr" to the file /etc/modprobe.d/blacklist.conf.  But, while this "works", it is not acceptable on my laptop since it permanently prevents any and all sounds (e.g. music) from playing on the machine.

Another thread, by ebe326 ([http://ubuntuforums.org/showthread.php?t=789858&highlight=restart+beep](http://ubuntuforums.org/showthread.php?t=789858&highlight=restart+beep)), indicating how to play a specific wave file on shutdown, gave me an idea of how to fix the "annoying beep" problem.  Use a bash script to temporarily turn off the speaker, and then issue the command to shutdown (or restart).

My kludge, therefore, it to use the following two script files (modified versions of ebe326's scripts), activated through program launchers (icons) on the display screen:


(1) shutdown.sh

#!/bin/sh
#Put your custom commands after this line

echo "Quiet system shutdown..."

# Temporarily disable the PC speaker

sudo /sbin/modprobe -r pcspkr

# The next line is the regular gnome logout command

sudo /sbin/shutdown -h now "Shut Down via gdm."


(2) restart.sh

#!/bin/sh
#Put your custom commands after this line

echo "Quiet system reboot..."

# Temporarily disable the PC speaker

sudo /sbin/modprobe -r pcspkr

# The next line is the regular gnome logout command

sudo /sbin/shutdown -r now "Rebooted via gdm."


As a sidenote, a benefit (for some) of this approach is that it also circumvents the 60-second countdown timer in the "Switch users or shut down" menu.  

Now, while this works for me, I'm stuck with two icons on my - otherwise - clean display.  So, here's my question.  How do I associate these batch files with the "Shut Down" and "Restart" options in the "Switch users or shut down" menu?  

If I go to System - Administration - Login Window - Edit Commands - Halt command (and, similarly, the Reboot command), I can browse to the folder with the batch file, and set the path and the file name as the command to be executed, and Apply Command Changes.  But, when I hit the Shut Down (or Reboot) option in the menu, the annoying beep once again accompanies the operation.  Evidently, this is not the way to the truth.

Can anyone point me down the right road - or - I will be stuck with my kludgy icons until a version of Ubuntu (ar a patch to Jaunty) fixes the problem elegantly!


p.s.  A patch may yet be forthcoming as work is on-going on this bug (see: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/331589](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/331589) with the latest post made on 10-Aug-09)

---

### Post by credobyte on 2009-08-15
Almost all Ubuntu versions have this beep by default. Sadly, "turn off system beep" was removed from sound settings since 9.04 :(

---

### Post by wojox on 2009-08-15
Google around for run levels. You should put the script in /etc/init.d/
Then something like 
```
sudo update-rc.d Myscript start nn 0
```

nn= numbered order to start up.
So 2 or something. Kind of the same way you start and stop other services. You need to know the proper run-levels. Not to sure about.

[http://www.cs.bgu.ac.il/~piavka/suse/ch13s04.html](http://www.cs.bgu.ac.il/~piavka/suse/ch13s04.html)

---

### Post by whitethorn on 2009-08-15
Cool not bad, just a small syntax problem

# The next line is the regular gnome logout command

> sudo /sbin/shutdown -h now "Shut Down via gdm."

shutdown -h   is not the halt command to stop the system not log out.  

As for setting the runlevel service, you'll need to write a script with 3 cases, start stop and restart before you can add it to the startup scripts in /etc/init.d/
after which you need to create symlinks to the file from the different runlevels found in /etc/rc1-5.d/ 

rc1.d is for scripts to be started in the first runlevel ...

---

### Post by Mardoct909 on 2009-08-15
Guys, just add

blacklist pcspkr

to /etc/modprobe.d/blacklist

It's gone forever once you restart.

---

### Post by centaurusa on 2009-08-15
wojox and whitethorn:

Thanks for the pointers.  Will check these out as my modified scripts need a bit more help than I thought.  They run fine in Terminal, but now (I was sure they were working earlier when I was testing them!) they won't run from the program launchers.  The main problem now is how to run scripts on commands requiring superuser permissions.  The Terminal scripts work, but require the user to enter a password.  Ideally, one would like a script to turn off the speaker and shutdown the machine without any further intervention - just like when you hit the Shut Down option on the menu.

Of course my other solution should work - overwrite 9.10 with 8.04 !

---

### Post by Mardoct909 on 2009-08-15
Run as root, solved for ever after reboot.

> echo blacklist pcspkr >> /etc/modprobe.d/blacklist

It puts the pc speaker into the blacklist, so it will never be used.

---

### Post by centaurusa on 2009-08-16
Jaunty beeps at restart... and shut down... and.. finally made it stop! (but, only by using - now - two inelegant kludges!) 
 
I finally have two application launchers on my desktop that will - quietly - shutdown and restart my machine.  

A note of caution - the method uses a no-password option to run xterm.  This is probably a security issue for some but - remember - the object of the exercise was to eliminate that annoying beep!

The modified script that shuts down the machine is as follows:


#!/bin/sh
#Put your custom commands after this line

echo "Quiet system shutdown..."

# Temporarily disable the PC speaker

sudo /sbin/modprobe -r pcspkr

echo "Speaker is disabled."

read

# The next line is the regular gnome shutdown command

sudo /sbin/shutdown -h now "Shut Down via gdm."


The read command seems to be necessary to have the application launcher run the script file.  The launcher is created by right-clicking on the desktop and selecting "Create Launcher".  The dialogue boxes are filled in as follows:

Name          Shutdown
Description   <Left blank>
Command       xterm -e ./quiet_shutdown.sh
Comments      Quiet shutdown by disabling the PC's speaker

The -e switch on the xterm command was noted by Sam at [http://ubuntuforums.org/showthread.php?t=33955](http://ubuntuforums.org/showthread.php?t=33955)

Now, because we need root permission to turn off the speaker and issue the shutdown command (and we want to avoid having to enter the root password) it's necessary to give the user permission to run xterm as root (see:  [http://serverfault.com/questions/49299/ubuntu-runing-sh-files-as-root](http://serverfault.com/questions/49299/ubuntu-runing-sh-files-as-root)).  We do this by modifying the sudoers file using the Terminal command (no quotes) "sudo visudo" and adding the line:

username  ALL = (ALL) NOPASSWD: /sbin/xterm

You enter your actual username (e.g. fred) rather than "username".  I'm not sure if the location of this line in the file is critical.  I put it after the two lines:

#User privilege specification
root   ALL=(ALL) ALL

The revised script for restart is:

#!/bin/sh
#Put your custom commands after this line

echo "Quiet system reboot..."

# Temporarily disable the PC speaker

sudo /sbin/modprobe -r pcspkr

echo "Speaker is disabled."

read

# The next line is the regular gnome reboot command

sudo /sbin/shutdown -r now "Rebooted via gdm."


A second application launcher, suitably modified to run this script file, takes care of the quiet restart process.

So, there you have it.  A kludge to turn off the speaker, and a kludge to run the script(s).  But, at least it's now quiet around here when I shutdown!

---

### Post by centaurusa on 2009-08-16
> The -e switch on the xterm command was noted by Sam at [http://ubuntuforums.org/showthread.php?t=33955](http://ubuntuforums.org/showthread.php?t=33955)

Oops.  Actually Sam suggested using the read command to make the terminal stay open for another application.  But this seems to work to run my two scripts from the application launchers.

The "xterm -e" idea came from:  [http://ubuntuforums.org/archive/index.php/t-1068922.html](http://ubuntuforums.org/archive/index.php/t-1068922.html)

---

### Post by Nate Shoffner on 2009-08-16
> **Mardoct909 said:**
> Guys, just add

blacklist pcspkr

to /etc/modprobe.d/blacklist

It's gone forever once you restart.

That's what I did and it worked.

---

### Post by centaurusa on 2009-08-16
> blacklist pcspkr
> That's what I did and it worked.

My problem with this particular solution is that it works just a little too well.  As I noted initially:

"...while this "works", it is not acceptable on my laptop since it permanently prevents any and all sounds (e.g. music) from playing on the machine."

I leave the speaker enabled until I go to shutdown (or restart), and then disable the speaker only temporarily - so avoiding the ear-splitting beep - but maintaining an ability to hear other sounds, play music, etc. on my laptop (with no external speakers) in a normal fashion.

---

### Post by mellowtothemax on 2009-09-05
> **Mardoct909 said:**
> Run as root, solved for ever after reboot.



It puts the pc speaker into the blacklist, so it will never be used.

This worked for me also, Ubuntu Jaunty on Dell Inspiron 8600.  But it should be an option in Sound Preferences.

---

### Post by bodhi.zazen on 2009-09-05
An alternate solution is:

```
sudo apt-get remove beep
```

---

### Post by r4lly on 2009-10-11
Thx mardock , it's solve my problem [IMG]http://ubuntuforums.org/images/icons/icon12.gif[/IMG]

---

### Post by bodhi.zazen on 2009-10-11
As an unrelated note, as an FYI , in karmic , 9.10, simply blacklisting is not enough.

I added this to /etc/rc.local

```
xset -b
```

---

