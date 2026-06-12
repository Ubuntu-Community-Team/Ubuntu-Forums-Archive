---
title: "Force grub to boot another OS once"
date: 2009-11-01
forum: General Help
---

### Post by alidm on 2009-11-01
I have a dual boot desktop with Ubuntu 9.10 as the primary, and Windows XP as the secondary boot options. I remotely connect to this machine and sometimes I need to switch back and forth between the two OS's. The problem is that I cannot remotely see the grub menu to select Windows at start-up. I am looking for a way to temporarily force the grub to boot into the second choice in the menu (just for the next restart), and afterwards it boots up in the first one as usual.

I found some workaround suggesting the command
```

sudo grub-set-default 1
sudo reboot

```
would automatically boot up in the second choice for the next reboot, though for some reason, I can't seem to get it to work on my system.

I used to use openSUSE for a while and there was a nice option in the system leave menu saying "Reboot in Windows". If you could guide me if there is any way to activate such a functionality in Ubuntu, that would also be great!

---

### Post by drs305 on 2009-11-01
> **alidm said:**
> 
I found some workaround suggesting the command
```

sudo grub-set-default 1
sudo reboot

```
would automatically boot up in the second choice for the next reboot, though for some reason, I can't seem to get it to work on my system.


The "grub-set-default" (run as root) works fine but there is a catch. In /etc/default/grub the default setting has to be "saved", i.e.:
DEFAULT=saved

Then you can use "grub-set-default X"  with X being either the numeric position of the menuentry you want to use (starting with 0) or the exact title of the menuentry (between the quotes).

Using "saved" will use the last successfully run system (which the grub-set-default command sets). You would have to run it again to reset it to your previous system. Seems like you could write a script that would run the command with the value you wanted to use. You could probably do the same by changing the value of DEFAULT in /etc/default/grub, but an advantage of the grub-set-default command is that you do NOT have to run "sudo update-grub" afterward for it to take effect.

---

### Post by alidm on 2009-11-01
> The "grub-set-default" (run as root) works fine but there is a catch. In /etc/default/grub the default setting has to be "saved", i.e.:
DEFAULT=saved

I changed /etc/default/grub as you advised, and now it looks like below:
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
GRUB_DEFAULT=saved
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```

I ran
```

sudo grub-set-default 1
sudo reboot

```
and grub automatically chose the second option (Windows). This fixed the problem in part, as the next time when I rebooted the system from Windows, grub still tried to boot up the second entry. Unfortunately, I was not able to change the grub-set-default from Windows and therefore there was no way to get back to Ubuntu remotely.

I think I need something to temporarily change the boot order just for the very next reboot, and afterwards I want everything in its normal state.

---

### Post by vaal12 on 2011-09-05
It works like this:
In /etc/default/grub
1. Set GRUB_DEFAULT to 
    GRUB_DEFAULT=saved

2. sudo update-grub

3. Set default OS to load (this will load every time you reboot machine, unless option 4 is used)
    sudo grub-set-default 0 

4. When need to load other OS (number is a menu number of OS as in /boot/grub/grub.cfg, this will load other OS only once during next reboot - reboot to be started manually):
   sudo grub-reboot 4

It works for me. More information on those commands @https://help.ubuntu.com/community/Grub2#Command_Line_and_Rescue_Mode



> **alidm said:**
> I changed /etc/default/grub as you advised, and now it looks like below:
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
GRUB_DEFAULT=saved
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```I ran
```

sudo grub-set-default 1
sudo reboot

```and grub automatically chose the second option (Windows). This fixed the problem in part, as the next time when I rebooted the system from Windows, grub still tried to boot up the second entry. Unfortunately, I was not able to change the grub-set-default from Windows and therefore there was no way to get back to Ubuntu remotely.

I think I need something to temporarily change the boot order just for the very next reboot, and afterwards I want everything in its normal state.

---

### Post by teeedubb on 2011-09-22
> **vaal12 said:**
> It works like this:
In /etc/default/grub
1. Set GRUB_DEFAULT to 
    GRUB_DEFAULT=saved

2. sudo update-grub

3. Set default OS to load (this will load every time you reboot machine, unless option 4 is used)
    sudo grub-set-default 0 

4. When need to load other OS (number is a menu number of OS as in /boot/grub/grub.cfg, this will load other OS only once during next reboot - reboot to be started manually):
   sudo grub-reboot 4

It works for me. More information on those commands @https://help.ubuntu.com/community/Grub2#Command_Line_and_Rescue_Mode

Thanks [vaal12]("http://ubuntuforums.org/member.php?u=1429710"), your method works flawlessly!!

---

### Post by sefs on 2012-09-09
I have some questions on this that I don't understand.

1/
Will this work if my grub2 is on a dedicated partition.

2/ What does this mean "unless option 4 is used" in point number "3."

2/ is sudo grub-reboot 4 going to load the 5th entry?

> **vaal12 said:**
> It works like this:
In /etc/default/grub
1. Set GRUB_DEFAULT to 
    GRUB_DEFAULT=saved

2. sudo update-grub

3. Set default OS to load (this will load every time you reboot machine, unless option 4 is used)
    sudo grub-set-default 0 

4. When need to load other OS (number is a menu number of OS as in /boot/grub/grub.cfg, this will load other OS only once during next reboot - reboot to be started manually):
   sudo grub-reboot 4

It works for me. More information on those commands @https://help.ubuntu.com/community/Grub2#Command_Line_and_Rescue_Mode

---

### Post by overdrank on 2012-09-09
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

