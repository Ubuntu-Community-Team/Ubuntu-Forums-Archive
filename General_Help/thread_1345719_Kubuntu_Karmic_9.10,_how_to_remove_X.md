---
title: "Kubuntu Karmic 9.10, how to remove X"
date: 2009-12-04
forum: General Help
---

### Post by dr_livsey on 2009-12-04
* When I had 9.04 I easily did that with command: "**sudo update-rc.d -f kdm remove**". After upgrade to 9.10 X starts again each boot automatically. 

* I tried the same command, but it doesn't do anything. Could you please explain to me how can I switch it off (remove auto load **kdm** at startup and have just command line)?

* Also I'd like to remove starting screen (black screen with blue "Kubuntu" and progress-bar). I'd like to have just command line, is it possible?

Thanks in advance!

---

### Post by sisco311 on 2009-12-04
Hi and welcome to the forums!

> **dr_livsey said:**
> * When I had 9.04 I easily did that with command: "**sudo update-rc.d -f kdm remove**". After upgrade to 9.10 X starts again each boot automatically. 

* I tried the same command, but it doesn't do anything. Could you please explain to me how can I switch it off (remove auto load **kdm** at startup and have just command line)?


The SystemV style init script in Karmic is replaced by an Upstart job (/etc/init/kdm.conf).

If you want to disable it simply rename the file:
```
sudo mv /etc/init/kdm.conf /etc/init/kdm.conf.noexec
```

Or edit the file to look like this:
```
  
description     "K Display Manager"
author          "Richard Johnson"  

start on ([B]never
          and[/B] filesystem
          and started hal
          and tty-device-added KERNEL=tty7
          and (graphics-device-added or stopped udevtrigger))
stop on runlevel [016]
...

```

To start it:
```
sudo initctl emit never
```
or:
```
sudo initctl start kdm
```

[http://upstart.ubuntu.com/getting-started.html]("http://upstart.ubuntu.com/getting-started.html")

> **dr_livsey said:**
> 
* Also I'd like to remove starting screen (black screen with blue "Kubuntu" and progress-bar). I'd like to have just command line, is it possible?

Thanks in advance!

Edit the /etc/default/grub file 
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
**GRUB_CMDLINE_LINUX_DEFAULT=""    #"quiet splash" removed**
GRUB_CMDLINE_LINUX=""
...

```

run:
```
sudo update-grub
```

[thread=1302743]Grub 2 - 5 Common Tasks[/thread]
[thread=1287602]Grub 2 Title Tweaks[/thread]
[thread=1195275]The Grub 2 Guide[/thread]

---

### Post by dr_livsey on 2009-12-05
**sisco311**, thank you very much for your detailed answer!

---

### Post by dr_livsey on 2009-12-07
**sisco311** Actually there is no file /etc/default/grub on my system, I tried searching file by content "quiet splash" and found only "/boot/grub/menu.lst". And this line is commented there.

At this moment I failed to switch off graphics at start up, but succeded with kdm! And that's already great!

---

### Post by sisco311 on 2009-12-07
Edit the /boot/grub/menu.lst file:
```
gksu gedit /boot/grub/menu.lst
```

and remove the *quiet* and *splash* kernel parameters from the end of the *kernel* lines.

i.e.:
```
title Ubuntu 9.10
root (hd0,0)
*kernel /boot/vmlinuz-<version> root=UUID=<uuid> ro **quiet splash***
initrd /boot/initrd.img-<version>
```  

and from the *# defoptions=**quiet splash*** line.

---

