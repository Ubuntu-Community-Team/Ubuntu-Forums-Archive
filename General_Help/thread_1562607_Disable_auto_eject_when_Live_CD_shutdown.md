---
title: "Disable auto eject when Live CD shutdown"
date: 2010-08-27
forum: General Help
---

### Post by lee321987 on 2010-08-27
Is there some file I can alter on the Live CD image that will make Ubuntu not automatically eject the drive tray when I shut down from a live CD session?

Thanks in advance.

=========================================================

[EDIT -- SOLVED]
Thanks to [dcstar]("http://ubuntuforums.org/member.php?u=7532") for linking me to:
[http://ubuntuforums.org/showthread.php?p=9904986#post9904986](http://ubuntuforums.org/showthread.php?p=9904986#post9904986)
/etc/rc0.d/S89casper is a link though, so I just edited the file it  points to (/etc/init.d/casper) -- seems to be working.  I merge a  modified "casper" at every boot, next time I build a Remastersys, I'll  try to make it permanent.

---

### Post by drs305 on 2010-08-27
I can't answer your question with absolute certainty, but since nobody else has responded I'll suggest something.

In a VM, I tried loading the LiveCD and pressed F6. It provided several options. Pressing F6 again provided some boot options, but "noeject" was not one of the preselected options. 

However, once I pressed F6 the boot command was visible and I was able to add "noeject" to the end of the boot options. You might try this to see if it does what you want.

I also posted because I was wondering what situation required you to request this option. If you regularly boot the LiveCD but also have Ubuntu installed on your computer, you can add the Ubuntu LiveCD ISO to your Grub2 menu. This would allow you to boot the LiveCD without having to insert the CD itself. Additionally, if accessed in this manner, the "noeject" option can be added to the Grub2 menuentry for the ISO.

If this is something you might want to do, let me know and I'll provide more information here or link you to the posts to help you accomplish this.

---

### Post by lee321987 on 2010-08-28
I tried.  The end of the boot options looked exactly like this:
```
-- noeject
```but the tray still ejected when I shut down.

You asked why I want to do this.  I keep a liveCD in my drive 99% of the time.  I do all my financial transactions in a liveCD environment.  I almost never need to take the CD out when I restart, but it ejects anyway.

Was I right to put the "noeject" after the "--"?

---

### Post by drs305 on 2010-08-28
lee321987,

I've done some more testing and here is what I'd recommend:

Put the following entries *noprompt noeject* after the two default ones (quiet splash) and before the " --". With further experimentation, I get to the Desktop by pressing F6, then ESC when it asks for the language, then F6 again. That reveals the command line entry. So the ending after the change would look like:  *quiet splash noprompt noeject --*

I think a better solution if you have Ubuntu installed is to make a custom entry to boot the ISO from your hard drive. Grub 2 can do this. The advantages to me are:
[LIST]
[*]You don't need to keep the CD inserted or need to change the BIOS boot order.

[*]You won't need to add the special option each time, since the command options will be included in the menuentry.

[*]It should boot a bit faster.
[/LIST]  

To add an ISO menuentry (assumes Ubuntu ISO is on sda5 - change the ISO name and (hdX,Y) designations if different):

Copy the ISO to your hard drive. I am going to put it in your /boot folder in a new folder called "iso"
```
sudo mkdir /boot/iso
sudo cp /<path>/ubuntu-10.04-desktop-i386.iso /boot/iso/

```

Open the Grub 2 custom file for editing:
```
gksu gedit /etc/grub.d/40_custom
```

Add the following:
> 
menuentry "Ubuntu ISO" {
loopback loop (hd0,5)/boot/iso/ubuntu-10.04-desktop-i386.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/ubuntu-10.04-desktop-i386.iso noprompt noeject
initrd (loop)/casper/initrd.lz
}
 

Save the file, then update grub:
```
sudo update-grub
```

---

### Post by lee321987 on 2010-08-28
It suppresses the prompt to remove the CD, but the tray still gets  ejected  (tried both before and after the "--" and both have same  effect).

I don't currently have an Ubuntu installed on any internal hard drives (just an external that I usually run a laptop with).  Anyway, I like knowing it's on a CD that can never be altered.

I have some experience building programs from source.  I could download  the Ubuntu source change it, and compile (if it's not _extremely_  difficult), if you know what to change.

Thanks for helping.

(why do my posts have a little smiling, red devil next to the subject?)

---

### Post by drs305 on 2010-08-28
Sorry, I don't know what the command to change if it's not one of the options we've already discussed. I'm away from home for the next week and don't have a LiveCD to play with. I'd hoped just having the "noprompt noeject" options would do the trick.

As for the icon, when you create a message if you scroll down below the entry there is a section to add the "Post icon". The little red devil is one of the options. Perhaps it remains until you select another or 'none'.

---

### Post by dcstar on 2010-08-28
> **lee321987 said:**
> 
.........
You asked why I want to do this.  I keep a liveCD in my drive 99% of the time.  I do all my financial transactions in a liveCD environment..


Then simply create a Live USB and use that - it will most likely be quicker than a CD anyway.

---

### Post by lee321987 on 2010-08-29
Thanks for the help, guys.

I'll keep an eye on this thread in case anyone finds anything new.

(btw I've selected "No Icon" before I submit this reply)

---

### Post by dcstar on 2010-09-02
> **lee321987 said:**
> Thanks for the help, guys.

I'll keep an eye on this thread in case anyone finds anything new.

(btw I've selected "No Icon" before I submit this reply)

[http://www.pendrivelinux.com/ubuntu-remove-the-prompt-to-eject-cd/](http://www.pendrivelinux.com/ubuntu-remove-the-prompt-to-eject-cd/)

---

### Post by Agent69 on 2010-09-02
If you can boot from a USB device, it really is the best way to go. I install Ubuntu and Arch Linux this way and it rocks.

---

### Post by dcstar on 2010-09-02
[http://ubuntuforums.org/showthread.php?t=1565624](http://ubuntuforums.org/showthread.php?t=1565624)

---

