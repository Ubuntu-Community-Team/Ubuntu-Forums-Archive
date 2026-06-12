---
title: "Grub2 waits for keypress after failed boot"
date: 2010-01-06
forum: General Help
---

### Post by DappereDodo on 2010-01-06
Hi all, just a question from a complete Linux noob. Last week I installed minimal Ubuntu Karmic with XBMC live on my HTPC. I'm connecting to my fileserver thru a wireless interface and although that works like a charm most of the time, every once in a while the interface doesn't come up during boot and the PC 'hangs'. 

I then press ctrl+alt+del and the pc reboots and the Grub2 boot menu appears, I suppose because the previous boot didn't go well. However, the boot menu doesn't have a timeout, I have to press <enter> to continue booting. My wireless USB-keyboard isn't working at that stage yet, so I'm unable to continue.

This is my /etc/default/grub
```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash xbmc=autostart,nodiskmount,setvolume loglevel=0"
GRUB_CMDLINE_LINUX=""
```How can I get it such that Grub always times out, even after a failed boot?

---

### Post by DappereDodo on 2010-01-07
kick. Anyone?

---

### Post by Leppie on 2010-01-07
at the end of your /etc/grub.d/00_header file, comment out the if condition except for the regular set timeout line like this:
```
#if [ \${recordfail} = 1 ]; then
#  set timeout=-1
#else
  set timeout=${GRUB_TIMEOUT}
#fi
```

run update-grub to regenerate the grub.cfg with the new settings:
```
sudo update-grub
```

reboot, now it should always boot the default option after the timeout, even if the previous boot failed.

suc6

---

### Post by DappereDodo on 2010-01-07
Excellent, thanks a million Leppie :D

---

### Post by Leppie on 2010-01-07
You're welcome, graag gedaan.

groetjes

---

### Post by wizel on 2010-01-09
I rather wanted to use a different approach and edited /boot/grub/grubenv to change recordfail to 0 (recordfail=0). Did work OK first time, but on the next boot recordfail was set to 1 again, and got same issue.

I could not discover what sets recordfail to 1.

---

### Post by meierfra. on 2010-01-16
> I could not discover what sets recordfail to 1.
Have a look at this: [recordfail]("https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:recordfail")

---

### Post by brycenesbitt on 2011-06-15
See also this thread:
[http://serverfault.com/questions/243343/headless-ubuntu-server-machine-sometimes-stuck-at-grub-menu](http://serverfault.com/questions/243343/headless-ubuntu-server-machine-sometimes-stuck-at-grub-menu)

---

### Post by jfollmann on 2012-05-15
Leppie's fix worked for me as well. I'm glad I finally found this thread, I've been trying to figure out what was wrong with my /etc/default/grub for about a full day now! Turns out, nothing was wrong with that file :)

And thanks to meierfra and brycenesbitt for the info on what this fix is doing exactly. It's good to know that I'm probably not causing any major harm by doing this.

---

### Post by oldos2er on 2012-05-15
Old thread closed.

---

