---
title: "I dont know the password and im using a mini laptop"
date: 2010-03-25
forum: General Help
---

### Post by Mikey Teh Zombe on 2010-03-25
i cant use wireless internet because of the stupid password restrictions and can only use ethernet, i want to either change the pass word or reinstall ubuntu and i cant use terminal to mount the iso to hopely try to reinstall it because of the damn password i dont know, and i dont know how to change it , any ideas

btw, i cant use disks

---

### Post by ProfessionalOPs on 2010-03-25
what ubuntu are u using?

---

### Post by ProfessionalOPs on 2010-03-25
are U THERE? Mikey Teh Zombe??? HELLO I MIGHT BE ABLE TO HELP

---

### Post by Mikey Teh Zombe on 2010-03-26
sorry my internet went out, system about says im running 8.04 please help

---

### Post by wojox on 2010-03-26
Try resetting it: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Mikey Teh Zombe on 2010-03-26
> **wojox said:**
> Try resetting it: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

i tap esc the whole time starting at the minute i power on until i reach desktop, it isnt working

---

### Post by llawwehttam on 2010-03-26
You must either be missing it or have a faulty keyboard.

Do you see grub flash up at all?

---

### Post by Mikey Teh Zombe on 2010-03-26
no i dont see it, how do i test my esc key?

---

### Post by aysiu on 2010-03-26
> **Mikey Teh Zombe said:**
> i tap esc the whole time starting at the minute i power on until i reach desktop, it isnt working In the most recent version of Ubuntu, you have to hold down the Shift key during bootup to get the Grub menu.

---

### Post by Mikey Teh Zombe on 2010-03-26
ok il try that real quick

---

### Post by aysiu on 2010-03-26
This wouldn't happen to be a Dell Mini, would it?

If so, this may help:
[http://blogs.gnome.org/mneptok/2008/11/11/reset-your-password-with-recovery-mode-on-the-dell-mini-9-netbook/](http://blogs.gnome.org/mneptok/2008/11/11/reset-your-password-with-recovery-mode-on-the-dell-mini-9-netbook/)

---

### Post by Mikey Teh Zombe on 2010-03-26
yes this is a dell mini.
i tried your shift method and it didnt work

---

### Post by macogw on 2010-03-26
You're not using the most recent version of Ubuntu, so AYSiu's comment was a bit misplaced ;-)

Do you see it say "GRUB Loading..." and countdown at the beginning? That's when you hit Esc.  If not, you could always do:
gksudo gedit /boot/grub/menu.lst and change the "hiddenmenu" setting so that it'll show the menu when it boots and then you can choose the other boot options you're being told.

Also: are you talking about your user's password, or the wireless's password?

---

### Post by Mikey Teh Zombe on 2010-03-26
once i select recory mode it says provide root password for maintinence 
i have a felling its not good' suggestions?

---

### Post by macogw on 2010-03-26
Did you manually set a root password at some point?  There should not have been one by default, so it should have taken you to a root shell immediately, unless you set one, in which case you're *almost* stuck, but not really.

You can make a bootable USB stick and boot from that, then mount the laptop's hard drive and edit the etc/shadow file on it so that on root's line, instead of the long hash that'll be there, it just has a ! or * like almost every other line.

---

### Post by Mikey Teh Zombe on 2010-03-26
im talking about changeing the usernames password

---

### Post by Mikey Teh Zombe on 2010-03-26
> **macogw said:**
> Did you manually set a root password at some point?  There should not have been one by default, so it should have taken you to a root shell immediately, unless you set one, in which case you're *almost* stuck, but not really.

You can make a bootable USB stick and boot from that, then mount the laptop's hard drive and edit the etc/shadow file on it so that on root's line, instead of the long hash that'll be there, it just has a ! or * like almost every other line.

oh god that sounds incredibly difficult.

---

### Post by aysiu on 2010-03-26
> **Mikey Teh Zombe said:**
> oh god that sounds incredibly difficult.
It's really not.

You can see a video on it here (scroll all the way to the bottom):
[http://psychocats.net/ubuntu/resetpassword](http://psychocats.net/ubuntu/resetpassword)

To make a bootable USB, just use UNetBootin:
[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

---

### Post by sisco311 on 2010-03-26
> **Mikey Teh Zombe said:**
> oh god that sounds incredibly difficult.

OKAY, then try this:

At the grub menu highlight the *Recovery Mode* entry,

press e for edit, highlight the *kernel* line & press e again,

remove the *ro single* kernel options from the end of the line 

and append it with *rw init=/bin/bash*, press Enter, then b too boot.

Wait for all the boot-up processes to finish.

Remount the root partition:
```
mount -o remount,rw /
``` 

Disable the root account password:
```
usermod -p ! root
```

Reset your user password:
```
passwd **username**
```
replace **username** with your login name.

Press Ctrl+Alt+Del to reboot.

---

### Post by Mikey Teh Zombe on 2010-03-26
i used unetbootin on my flashdrive but its not booting at startup, any ideas?

btw, can i just completly reinstall ubuntu if i can get my flash drive to boot?

---

### Post by Mikey Teh Zombe on 2010-03-26
> **sisco311 said:**
> OKAY, then try this:

At the grub menu highlight the *Recovery Mode* entry,

press e for edit, highlight the *kernel* line & press e again,

remove the *ro single* kernel options from the end of the line 

and append it with *rw init=/bin/bash*, press Enter, then b too boot.

Wait for all the boot-up processes to finish.

Remount the root partition:
```
mount -o remount,rw /
``` 

Disable the root account password:
```
usermod -p ! root
```

Reset your user password:
```
passwd **username**
```
replace **username** with your login name.

Press Ctrl+Alt+Del to reboot.

is there a video of this method?

---

### Post by macogw on 2010-03-26
> **Mikey Teh Zombe said:**
> 
btw, can i just completly reinstall ubuntu if i can get my flash drive to boot?

Yes

---

### Post by Mikey Teh Zombe on 2010-03-26
> **macogw said:**
> Yes

okay, but my flash drive wont boot aat start up, is there anyway to fix it?

---

### Post by macogw on 2010-03-26
Check the BIOS settings at the start to see if USB is the first option? If not, make it the first.

---

