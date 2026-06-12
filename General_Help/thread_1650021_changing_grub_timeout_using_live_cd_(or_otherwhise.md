---
title: "changing grub timeout using live cd (or otherwhise)"
date: 2010-12-20
forum: General Help
---

### Post by sundays211 on 2010-12-20
hi

I have accidentally changed the grub timeout to 0 seconds. My default boot is also set to windows xp so there is currently no possible way to boot into ubuntu. Could someone please tell me how to change the grub timeout without needing to startup into Ubuntu. Thank you in advance.

---

### Post by karthick87 on 2010-12-21
Boot using a live cd and then edit the grub file,

```
 sudo gedit /etc/default/grub
``````
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=saved
GRUB_HIDDEN_TIMEOUT=0
#GRUB_HIDDEN_TIMEOUT_QUIET=true
[COLOR=Red]GRUB_TIMEOUT=10[/COLOR]
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="ipv6.disable=1"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```Search  the line [COLOR=Red]GRUB_TIMEOUT=10[COLOR=black] and[/COLOR] [COLOR=black]change the value.And then update grub..
[/COLOR][/COLOR]```
[COLOR=Red] [COLOR=Black]sudo update-grub[/COLOR]
```[/COLOR][COLOR=Red][COLOR=black]
[/COLOR][/COLOR]

---

### Post by sundays211 on 2010-12-21
I guess I will need to go about mounting the file systems with the live CD. Where should I mount What?(note that I have a separate boot and home partion)

---

### Post by sundays211 on 2010-12-21
using the usual method of mounting all my file systems under /mnt/root (/boot to /mnt/root/boot) and then running chroot /mnt/root would not let me run update-grub. the error message:```
/usr/sbin/grub-prob: error: cannot find a device for / (is /dev mounted?).
``` appears. 

I hope this does not mean I need to manually edit the /boot/grub/grub.cfg file

---

### Post by stinkeye on 2010-12-21
See this thread for editing your grub.cfg from a live cd.
[**_[COLOR="DarkRed"]http://ubuntuforums.org/showthread.php?t=1567456[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1567456")
The last post gives a summary of the method

Edit the **set timeout=** value in /boot/grub/grub.cfg, save and reboot.
eg ```
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  [COLOR="DarkOrange"]set timeout=10[/COLOR]
```



When your back in your Ubuntu install edit your /etc/default/grub file
```
gksudo gedit /etc/default/grub
```

changing the **GRUB_TIMEOUT=** value to whatever you want and save.

Then run 
```
sudo update-grub
```
This will overwrite the change you made previouslly in /boot/grub/grub.cfg

---

### Post by stinkeye on 2010-12-21
I've just been playing around with the live cd and you can also do it this way.

Boot to the live cd.

Click on Places in the Menubar and
choose the appropriate entry for your ubuntu install and click on it.


Open up a terminal and enter
```
gksu nautilus
```
and you should see your Ubuntu partition mounted in the left pane.

Click on it and navigate to /boot/grub
Open **grub.cfg ** and edit and save as described before.

Then do the second step once rebooted and in your Ubuntu install.

---

### Post by sundays211 on 2010-12-22
Thanks :D

editing the grub.cfg time-out has allowed me to successfully boot in Ubuntu again.

I think I will stick with the 10 second time-out. however, I know I will need to edit the /etc/default/grub file as well so that it doesn't screw up next time update-grub is run

---

