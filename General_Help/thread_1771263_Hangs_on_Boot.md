---
title: "Hangs on Boot"
date: 2011-05-30
forum: General Help
---

### Post by poliltimmy on 2011-05-30
I have been having a problem with Ubuntu 10.04 hanging on boot. Some times it hangs on the splash screen and sometimes I get to the desktop, but there is no panel, desktop icons or mouse cursor. If I hard reboot (hold the power button in until shut down) it will come on and work fine after that.

I do not not know if this could be related but Transmission stopped working about the same time. Tried reinstall already. The Transmission box pops up but not the add prompt.  Weird I know.

I tried yesterday to update to 10.10 to see if this would fix it. The upgrade went fine. I elected to replace the config files that it asked about to see if that would over write and possibly fix it. Needless to say, I am lost now.

---

### Post by hwttdz on 2011-05-30
I'd recommend changing the grub boot options from "quiet splash" to "".  That way you'll be able to see where in the boot process it's possibly hanging (I don't understand why those are the defaults).

---

### Post by poliltimmy on 2011-05-30
Thanks hwttdz. Could you tell me how to do this step. I have never had this kind of problem before.

---

### Post by hwttdz on 2011-05-30
sudo gedit /etc/default/grub
and change "quiet splash" to ""
then run sudo update-grub
then reboot, and you'll see the whole boot process.  It might also help to post dmesg from a boot where you don't get your whole desktop.  Also there are no error messages when it boots, but acts strangely?

You might want to remove transmission for the time being just to reduce the number of variables.

---

### Post by poliltimmy on 2011-05-30
Correct there are no error messages. How do I get a terminal for dmesg output? Since this is only happening on a cold start. Any restart I do i.e. update restarts it boots fine. That is why I am so confused. Will run commands you post but I will have to let the box cool back down before I know if it works or not.

$ sudo gedit /etc/default/grub
[sudo] password for timmy: 


$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found linux image: /boot/vmlinuz-2.6.32-31-generic
Found initrd image: /boot/initrd.img-2.6.32-31-generic
Found memtest86+ image: /boot/memtest86+.bin
done

It appears it updated.

sudo apt-get remove transmission
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package transmission is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libindicator0 python-evince libavutil-extra-49 python-gnomedesktop
  libgnomeprint2.2-data python-metacity python-mediaprofiles libappindicator0
  python-bugbuddy python-totem-plparser python-evolution libgnomeprint2.2-0
  libgnomeprintui2.2-0 libgnomeprintui2.2-common python-gtop libgnomecups1.0-1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
 
Should I autoremove as suggested?

Seems Transmission was still there. Removed with Synaptic.

---

### Post by poliltimmy on 2011-05-30
OK on a cold start the last line is ...

Setting System Sensors.......[ok]

Then locks up. As before a hard reboot it works.

---

### Post by poliltimmy on 2011-06-19
Any one have any idea what might be happening here. I ran memtest. No errors. Fresh install no change. I'm lost.

---

### Post by poliltimmy on 2011-06-23
After finally getting to the desktop after about 3 or 4 hard reboots, when I try to start an app, I get the cursor locked in upper left corner and a frozen screen. 

What confuses me is an update to 10.04.1 in April, was flawless. When it went to 10.04.2 I got this problem.
 
Graphics card is GeForce 8400GS (supposedly supported out of the box)
Mouse is mi usb optical model PD525P 

Makes no difference if I use legacy or nvidia driver. 


Right now I am back to 9.10, because an outdated Ubuntu box is still better than an updated Windows box!

---

### Post by poliltimmy on 2011-06-30
I have a successful install using the kernel install method. Yay!

---

