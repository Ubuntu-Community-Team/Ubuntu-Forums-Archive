---
title: "Ubuntu hangs on boot"
date: 2010-07-02
forum: General Help
---

### Post by tmk1944 on 2010-07-02
I have a Dell desk top PC, running WinXP and Ubuntu 10.04 LTS with a Ge-Force FX 5200 video card. In trying to get both monitors to work properly I thought it would help to reinstall Nvidia binary X.Org driver V173. After I removed the driver I tried to restart the computer with Umbuntu,    it hangs up at the Ubuntu logo. I can boot with the live disk, I also tried to reinstall the Nvidia driver But the machine still will not boot from the hard drive, it will boot into Win XP normally.  
 

 Should I just reinstall Ubuntu or fix the problem I created? My skills working in Terminal are minimal.
 Thank you for any help that you can give me,
 Roger

---

### Post by davidmohammed on 2010-07-02
try booting ubuntu but into recovery mode.  When requested, use the root terminal shell.

then type the following

sudo apt-get --purge remove nvidia-*

sudo apt-get install nvidia-current

---

### Post by tmk1944 on 2010-07-02
I am not able to get into the “recovery mode” or find “root shell”. I started ubuntu then pushed ESC but there was no option for recovery mode. How do I find recovery mode?

---

### Post by NUboon2Age on 2010-07-02
to get to the Grub2 menu (and be able to thereby be able to choose to boot into recovery mode) hold the shift key down during reboot.

You might want to go to #ubuntu or #ubuntu-beginners irc channels for further assistance.  If you don't have an irc client set up, you can use [http://webchat.freenode.net](http://webchat.freenode.net) for example (though sometimes the #ubuntu channel won't let unregistered nicknames sign in).

---

### Post by tmk1944 on 2010-07-03
[SIZE=3]*I have got to “recovery mode” and typed  in 'sudu apt-get –purge remove nvidia-*' pressed enter, and get 'command not found'  (two dashes between get and purge). Also tried with one dash between get and purge with same results.*[/SIZE]
 [SIZE=3]*I also tried ' repair broken ---' some or another and I was able to boot in normal Ubuntu with the same problem that I had before I removed nvidia driver. *[/SIZE]

---

### Post by dino99 on 2010-07-03
if someone give a command to run into a terminal, the best you can do is to avoid mistakes, better to copy/paste

---

### Post by oldfred on 2010-07-03
I do not think the command is purge remove

From the man page:

purge
           purge is identical to remove except that packages are removed and purged (any configuration files are deleted too).

---

### Post by tmk1944 on 2010-07-03
[SIZE=3]I have my computer up and running thanks to all that helped to get me looking in the right direction . But I still have a video driver problem that will have to wait for me to get home next week.[/SIZE]
[SIZE=3]Thanks to all,
Roger[/SIZE]

---

