---
title: "/etc/timidity permissions?"
date: 2010-12-14
forum: General Help
---

### Post by joegumbo on 2010-12-14
Hi,

I'm running Ubuntu 10.04 32-bit.  Sometimes I have difficulty starting X.  The system complains that "/etc/timidity" is not owned by me.  Then the system locks up.  

I checked the permissions.  'root' is both owner and group.  

Should I change the permissions to my username and/or my usernamegroup? Or, chown and chgrp to root again?

I would experiment on my own with this, but since the system already locks up sometimes, I don't want to find myself with an unusable system.

Thanks,
-Joe

---

### Post by kukker32 on 2010-12-14
you can change the file permissions as you want without harming anything..

but aware that if there are more than just you using the computer it might be a bad idea since not everyone knows what they are doing...


to change file permissions..

log in as root user,,

run this in termnial

sudo  <name of your file browser>
   nautilus in ubuntu
   dolphin in kubuntu
   thunar in xubuntu

you can now change the permissions by right clicking and under the permissions tab..

hope it helps..

---

### Post by joegumbo on 2010-12-14
Hi kukker32,

I just changed the permissions to my username.  Then, rebooted.

I got the same complaint: " Home directory /etc/timidity not ours"

This time startx worked, though.

Btw, I did check my home directory and there is no 'etc/timidity' directory or 'timidity' directory.

Thanks,
-Joe

---

### Post by viragoboy on 2011-02-05
I ran into this as well today, I guess my ubuntu box is so stable I rarely reboot it {cough - windows}.
I noticed that many directories in /etc have application group ownership, but timidity had root, so I fired up nautilus as sudo and changed it. 

old
```
drwxr-xr-x  2 root    root        4096 2011-02-05 11:43 timidity
```

new
```
drwxr-xr-x  2 root    timidity    4096 2011-02-05 11:43 timidity
```

Rebooted, problem gone.

---

### Post by PaulWhipp on 2011-03-04
I have just seen this error as well on 10.04 following bringing the system up to date (as of March 5 2011) with routine updates.

On restart (prompted by the updates - my system is up 24/7 normally) X did not start immediately and I was dropped to a console login. This is something I've seen before once or twice but as I started to login in
"/etc/timidity not ours" flashed up and then the system started X and gnome normally.

I did another restart and the problem did not occur so it seems to have sorted itself out.

```

~ $ ls /etc -l | grep timidity
drwxr-xr-x  2 root    root     4096 2010-09-10 06:36 timidity

```

File permissions don't appear to be the issue in my configuration.

---

### Post by QuimNuss on 2012-12-23
THis is a reported bug, but I haven't found a workaround that works.

[old] [https://bugs.launchpad.net/ubuntu/+source/timidity/+bug/531733](https://bugs.launchpad.net/ubuntu/+source/timidity/+bug/531733)
[https://bugs.launchpad.net/ubuntu/+source/timidity/+bug/1035592](https://bugs.launchpad.net/ubuntu/+source/timidity/+bug/1035592)

Timidity does not own the /etc/timidity directory and this leads to a black screen and unusable system. I can get most of the times to a console by setting the nomodeset mode on grub

Changing home directory of timidity to /var/run/timidity does not work (actually that directory does not exist)

any ideas?

---

### Post by rnerwein on 2012-12-23
> **QuimNuss said:**
> THis is a reported bug, but I haven't found a workaround that works.

[old] [https://bugs.launchpad.net/ubuntu/+source/timidity/+bug/531733](https://bugs.launchpad.net/ubuntu/+source/timidity/+bug/531733)
[https://bugs.launchpad.net/ubuntu/+source/timidity/+bug/1035592](https://bugs.launchpad.net/ubuntu/+source/timidity/+bug/1035592)

Timidity does not own the /etc/timidity directory and this leads to a black screen and unusable system. I can get most of the times to a console by setting the nomodeset mode on grub

Changing home directory of timidity to /var/run/timidity does not work (actually that directory does not exist)

any ideas?
hi
some error messages. you said the directory dosen't exist. just create it and give the dir the permissions and owner suitable to that software.
some error messages (/var/log ?) would be useful.
cheers

---

### Post by QuimNuss on 2012-12-23
Hi rnerwein,

it's difficult to post anything since the system is very unusable. 2/3 boots ends up in black screen, 1/3 I succeed into getting to a console since the startx tty hangs when timidity daemon tries to start. Then I am able to switch to other non-graphical tty. (I am writing from another computer)

I'm on 12.04 and I upgraded yesterday from 10.04 after a lot of pain. I believe I have a pretty much messed up system (unity did not have half of the indicators installed!).

Anyway, which file at /var/log would be informative?

How can I get to a usable console on recovery mode? (readable file-system, network would be nice (network option did not return!))

I'll try your suggestion of creating the directory, but I feel the files inside /etc/timidity are going to be required. I don't see why would that work. Moreover, i've tried changing the owner of /etc/timidity to timidity:timidity, same result.

I've tried purging timidity, I'll let you know what that gives.

This is going to be hard...

---

### Post by rnerwein on 2012-12-23
> **QuimNuss said:**
> Hi rnerwein,

it's difficult to post anything since the system is very unusable. 2/3 boots ends up in black screen, 1/3 I succeed into getting to a console since the startx tty hangs when timidity daemon tries to start. Then I am able to switch to other non-graphical tty. (I am writing from another computer)

I'm on 12.04 and I upgraded yesterday from 10.04 after a lot of pain. I believe I have a pretty much messed up system (unity did not have half of the indicators installed!).

Anyway, which file at /var/log would be informative?

How can I get to a usable console on recovery mode? (readable file-system, network would be nice (network option did not return!))

I'll try your suggestion of creating the directory, but I feel the files inside /etc/timidity are going to be required. I don't see why would that work. Moreover, i've tried changing the owner of /etc/timidity to timidity:timidity, same result.

I've tried purging timidity, I'll let you know what that gives.

This is going to be hard...
hi
real single user mode from grub - how to
#--------------------------------------------------------------------------
# boot into single user mode you edit the boot instructions for the GRUB menu
# entry you wish to boot and add
# the kernel parameter/option single. Brief instructions for how to do
# this are below.

  1. Select (highlight) the GRUB boot menu entry you wish to use.
  2. Press e to edit the GRUB boot commands for the selected boot menu entry.
  3. Look near the bottom of the list of commands for lines similar to
     linux /boot/vmlinuz-3.2.0-24-generic root=UUID=bc6f8146-1523-46a6-8b\
     6a-64b819ccf2b7 ro quiet splash initrd /boot/initrd.img-3.2.0-24-generic
  4. Change the middle line in (3) by adding the kernel boot parameter single
     to the end of the ( and change "ro" to "rw" )
     line (i.e. after ro quiet splash).
     ==> ..... rw quiet single splash

        For this example you would change
            6a-64b819ccf2b7 ro quiet splash
          to
            6a-64b819ccf2b7 rw quiet splash single
   5. Press either Ctrl+X or F10 to boot using these kernel options.
      Note: These changes are [COLOR=Red]not persistent[/COLOR]. Any change to the kernel boot
      options made this way
      will only affect the next boot and only if you start that boot by
      pressing either Ctrl+X or F10
      while still in GRUB edit mode.

cheers

---

### Post by overdrank on 2012-12-23
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

