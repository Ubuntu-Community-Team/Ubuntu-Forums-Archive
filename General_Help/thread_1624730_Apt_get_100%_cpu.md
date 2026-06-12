---
title: "Apt get 100% cpu"
date: 2010-11-18
forum: General Help
---

### Post by freshmeatz on 2010-11-18
Keep getting this from time to time, I can kill the process,"apt-get -qq -y update" but will remain until then. is there a similar thread? searched , but probably used wrong search terms..

---

### Post by dino99 on 2010-11-18
try: sudo dpkg --configure -phigh -a

---

### Post by freshmeatz on 2010-11-18
> :~$ sudo dpkg --configure -phigh -a
dpkg: conflicting actions -p (--print-avail)

I already killed the process after stopping it and lowering the priority etc in attempt to figure it out, must be on a scheduled time dunno where, lol
will try again once it starts up again, usually once or twice a day.

---

### Post by dino99 on 2010-11-18
ah, my bad, its:

sudo dpkg-reconfigure -phigh -a

---

### Post by freshmeatz on 2010-11-18
> :~$ sudo dpkg-reconfigure -phigh -a
update-rc.d: warning: /etc/init.d/acpi-support missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
acpid stop/waiting
acpid start/running, process 11470
 * Starting AppArmor profiles                                                                         Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                                               [ OK ]
 * Reloading AppArmor profiles                                                                        Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                                               [ OK ]
stop: Unknown instance: 
start: Job failed to start
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 2
gpg:              unchanged: 2
atd stop/waiting
atd start/running, process 11839
avahi-daemon stop/waiting
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service dbus force-reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload dbus
avahi-daemon start/running, process 11890
update-alternatives: using /usr/share/man/man7/bash-builtins.7.gz to provide /usr/share/man/man7/builtins.7.gz (builtins.7.gz) in auto mode.
 * Disabling additional executable binary formats binfmt-support                               [ OK ] 
 * Enabling additional executable binary formats binfmt-support                                [ OK ] 
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service dbus force-reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload dbus
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service udev reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload udev
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
Updating certificates in /etc/ssl/certs... 0 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d....
updating keystore /etc/ssl/certs/java/cacerts...
done.
done.
Your console font configuration will be updated the next time your system
boots. If you want to update it now, run 'setupcon' from a virtual console.
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
cron stop/waiting
dpkg-maintscript-helper: error: couldn't identify the package


Does the process have to be running ? If so I can get it when it comes around again :) ran the same command "sudo apt-get -qq -y update" in a term with no issues, 
thanks for the info..

---

### Post by mcduck on 2010-11-18
> **freshmeatz said:**
> Keep getting this from time to time, I can kill the process,"apt-get -qq -y update" but will remain until then. is there a similar thread? searched , but probably used wrong search terms..

apt-get using 100% CPU is normal, it's just a question *how long it lasts*.

It will do that when checking for updates. If you just let it run for a while it will get the job done and the CPU usage will drop again.

Of course if it doesn't drip after some time there is something wrong. But since you only mentioned apt running at 100% it's impossible for us to tell if it's just a question of apt calculating your normal updates or something else.

---

### Post by freshmeatz on 2010-11-18
true, it was running all night, started about 11 pm, lasted till I killed it about 8 hours or so. hopefully it is dripping Maxwell House.

---

### Post by mcduck on 2010-11-18
> **freshmeatz said:**
> true, it was running all night, started about 11 pm, lasted till I killed it about 8 hours or so. hopefully it is dripping Maxwell House.

oh, in that case it definitely is a problem.

(I just had to make sure, since I've helped people n past with the similar issue and in the end they were just killing apt-get after less than a minute, interrupting the normal update check every time. But it definitely shouldn't take 8 *hours* to check the updates... :D)

---

### Post by freshmeatz on 2010-11-18
yeah that is what I was thinking, I know my update settings look for the cd rom while rechecking updates, I'm wondering if the rom is not in the drive at the time of the scheduled update and that is causing the hang time. since the rom was out when this took place. just a thought .

---

### Post by caradeporra on 2010-12-15
For those who find this thread trying to end your apt-get process because it is not stopping and taking up a high-percentage of your cpu - 

Open up your system monitor and go to processes tab.  Click 'View' and choose 'All Processes' (default shows just processes by the current user)  Now apt-get will show up and you can end it.

Carade

---

### Post by ibonyun on 2010-12-24
I'm tired of sudo killing apt-get EVERY morning.  How do I prevent this from happening in the first place?  What it causing it to start and stall?

---

### Post by makda on 2010-12-27
(bump)

having the same issue here and it seems to have started occuring a couple of days ago.

the command line appears to be :-
[INDENT]apt-get -qq -y[/INDENT]
and I am guessing that it is being called by the **update manager**

---

### Post by caradeporra on 2010-12-29
I believe you are correct, that it is the Update Manager.  Quick fix would be to go to
 System --> Administration --> Update Manager --> Settings
From here you can change how often it checs for updates ( I am guessing you have it set to check every day)

Fix fix would be to find which source is causing it to loop and remove that source.  Have you added any third-party sources?  Chances are if you have been using it a while you have, and perhaps one of them is no longer around or something like that, just a guess though.

Mine only happened once and now it is ok.

---

### Post by bluefrog on 2010-12-29
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/672436](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/672436)

---

### Post by calif99x on 2011-02-10
I am running 10.10 release version and getting this problem.  I noted that my system was very sluggish and top showed apt-get consuming 100% of the CPU with 75+ minutes of CPU time.  

Definitely looks like a bug as downloading the entire release image did not take that long.

From launchpad bug reports  [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/665580](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/665580) it appears that someone found a solution.  Link to the solution is given as [http://ubuntuforums.org/showthread.php?t=1593135](http://ubuntuforums.org/showthread.php?t=1593135)

Regards
Sandeep

---

