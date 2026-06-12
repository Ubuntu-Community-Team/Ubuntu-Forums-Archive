---
title: "change boot up sequence"
date: 2010-11-10
forum: General Help
---

### Post by ScoutL3 on 2010-11-10
To change the boot up sequence of Ubuntu and XP I opened the terminal in  Ubuntu and entered ( Sudo gedit /boot/grub/menu.lst ) in the command line and  pressed <ENTER> , another line ask me for password and when I try to enter  it , nothing happens , the cursor just blinks.Can someone tell me what I am  doing wrong.

---

### Post by irv on 2010-11-10
The easy way to do this is go to System> Administration> StartUp-Manager. Enter your password. When the program opens just select the Default OS from the drop-down-menu. Just close the program down and the next time you boot what you selected should be the Default OS.

---

### Post by Bearly Able on 2010-11-10
I don't think you're doing anything wrong, ScoutL3.  When you type your password in a terminal, nothing does show up, but if you press "enter" after typing, it should proceed with your command.  It's a bit disconcerting when you first encounter it.

---

### Post by oldfred on 2010-11-10
Version 9.04 and upgrades from that were the last to use menu.lst from grub legacy. Grub2 uses grub.cfg but you do not edit grub.cfg but rebuild it after any changes to parameter or menu files.

As irv has mentioned, Startup manager (SUM) in synaptic will allow you to set boot default and the timeout even with grub2.

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)
Download and install "StartUp-Manager from Synaptic package downloads. It will be listed under System/Administration menu. You can set it to default with Ubuntu (different versions) or Windows. You can also set the start up time in seconds.
[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)

SUM is the easiest way to change boot order, but you can change /etc/default/grub adn run sudo update-grub.

 GRUB 2  has three main parts plus a boot loader installed to the MBR:

   1. /etc/default/grub - the file containing GRUB 2 menu settings.
   2. /etc/grub.d/ - the directory containing GRUB 2 menu creating scripts.And a place for totally custom entries 40_custom.
   3. /boot/grub/grub.cfg - the GRUB 2 configuration file, not editable.

---

### Post by ScoutL3 on 2010-11-11
I installed startup manger and that worked well . Thankyou for the help.

---

### Post by irv on 2010-11-11
> **ScoutL3 said:**
> I installed startup manger and that worked well . Thankyou for the help.

Don't forget to see the bottom of oldfread's post #4, and mark this one solved.

---

