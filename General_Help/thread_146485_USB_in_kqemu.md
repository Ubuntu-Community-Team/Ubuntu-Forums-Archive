---
title: "USB in kqemu"
date: 2006-03-18
forum: General Help
---

### Post by Moonhill on 2006-03-18
I tried KQEMU with win2k. Everything works just fine but usb.
SInce qemu 0.8.0 provides usb option, I tried '-usb -usbdevice /dev/sdc1 or /media/usbdisk' which failed all. Do I have to enable it when I compile qemu? Thanks.

Other questions....

1. /dev/shm
If I want to use 512m for KQEMU WIN2K, I had to mount this /dev/shm as instructed. Is it ok to leave this /dev/shm 528m? Or should I release after job in order to sppedup other general performance?

2. Samba in KQEMU
I tried to connect KQEMU and host breezy through samba in order to share files. I setup samba daemon and other settings in the host and used 'smb \\smbserver\qemu' but I couldn't find any connections in the guest network. Anything I missed? Or anything critically important?

3. Compatibility between openoffice write and MS Word
Are they reasonably compatible according to your experience?

4. ATI Raden 7500 VIVO
I'd like to watch TV through TV Time using 'vido-in' on ATI Radeon 7500 vivo. How can I activate /dev/video0 or video-in function?

5. Kino and DV
I captured DV from my Sony DCR PC-7 using Kino. But the output captured video was not as good as that of what I normaly get from movie maker in windows system. It looks it lost lots of frames so that it looks quite jerky and terrible audio. Any setting I should consider? 

Thanks.

---

### Post by ajmacca on 2006-03-18
In terms of getting samba to work, try passing the smb option to qemu when you launch it.  Just add "-smb" somewhere to the command.  To access your samba shares, try clicking start->run then running "\\10.0.2.4" or "\\10.0.2.4\<samba share name".  I'm not 100% if this works because sadly I can't boot into Linux at the moment.

For usb, you can open up a command line or monitor in qemu (I can't remember how, possibly "ctrl-alt-1" or "ctrl-alt-F1" - make sure you have qemu selected for the second one!  If you try ctrl-alt-F1 and end up at a command line asking you to log into Linux, just hit ctrl-alt-F7 and everything should be back.  Once there, try something along the lines of:

[INDENT]"info usb" should list the devices that are attached to the host system
"usb_add <device>" lets qemu use the device[/INDENT]

Again, I apologise I can't test these and make sure.  If you can get into that command line for qemu, you can access a help file that should give you more concrete instructions on how to use the commands.  Failing that, if someone can tell me how to fix my problem I can check them for you!

---

### Post by Moonhill on 2006-03-19
Thanks. I'll try and post if there meets any problem.

---

### Post by Moonhill on 2006-03-20
Thanks.
I tried samba again...
In my case, I used qemu -smb \\moonhill\public, and in kqemu win2000, I ran '\\10.0.2.4\public' in the start>run. It worked fine.

But in case of usb, I failed. I'll try again. I started kqemu win2000 and used ctl+alt+f1 to see ubuntu console login screen and just pressed ctl+alt+f7 and typed 'info usb' in the terminal without anything about usb.

---

### Post by ajmacca on 2006-03-21
With the USB commands, the console for qemu is accessed by ctrl-alt-2 I've since found out.  Once you're done with the console, ctrl-alt-1 will get you back to windows 2000 (or whichever OS you're running in qemu).  Sorry about the confusion there, I wasn't able to test out what was right, and I didn't have time to find the correct command.

Here is a link to the QEMU documentation's section on USB devices:

[http://fabrice.bellard.free.fr/qemu/qemu-doc.html#SEC28]("http://fabrice.bellard.free.fr/qemu/qemu-doc.html#SEC28")

There's an example there about adding a device.  I successfully got XP to recognize my printer in QEMU, but it was unable to install the device.  So just a warning that your device might not be useable, even if you get windows 2000 to see it.  Anyways, I hope this helps you further!

---

### Post by barmaley on 2006-03-28
Hello, people

I have installed Win2k with qemu/kqemu and due to your advices I have also managed to see my directories in windows via SAMBA, though no success with USB. Did you manage to see USB key in windows?

Can I copy files from windows (running with qemu) to ubuntu? Probably not, but if there is some way, please tell me.
Thank you.

---

### Post by DarkManX4lf on 2006-05-08
yeah i also tried to get the usb to work by the link qemu usb info link [http://fabrice.bellard.free.fr/qemu/qemu-doc.html#SEC28](http://fabrice.bellard.free.fr/qemu/qemu-doc.html#SEC28) and it wouldnt work, it  keeps telling me

could not add usb device

im putting the host and the numbers in correctly but it just wont work...

are there other ways to get files from  ubuntu into qemu ?

---

### Post by mbsullivan on 2008-01-11
Although this thread is rather old, a possible solution to a similar USB issue (for Gutsy users) follows:

Qemu (and vmware) may not emulate usb devices correctly if /proc/bus/usb is not working.  By default, /proc/bus/usb will not reflect the connected USB devices under Gutsy.  In order to fix this, uncomment lines 42-45 of /etc/init.d/mountdevsubfs.sh, as per the directions [here]("http://ubuntuforums.org/showpost.php?p=3857344&postcount=4").

Then, restart mountdevsubfs.sh with the following command (or restart your computer):

```
sudo /etc/init.d/mountdevsubfs.sh start
```

Following this, /proc/bus/usb should be populated, and your USB devices should work under Qemu.  

Hope this helps somebody!
Mike

---

