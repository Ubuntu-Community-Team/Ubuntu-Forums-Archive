---
title: "Computer Crashed-Now will not Boot (full error msg below)"
date: 2011-01-30
forum: General Help
---

### Post by elizamach on 2011-01-30
I have a rebuilt compaq laptop. I installed ubuntu about a month ago and it worked fine until the other day. 

Message below is what I get when I go to "edit" at the screen where it allows me to choose which version of Ubuntu to run (I get other errors when selecting any version listed....so I'm doing one thing at a time here.)

"recordfail
insmod part-msdos
insmod ext2
set root=' (hd0,msdos1)'
search --no-floppy --fs-uuid --set b5a79df1 -0fd3-4431-81ac-3898fe436/f37
linux /boot/vmlinuz-2.6.35-24-generic root=UUID=b5a79df1-0fd3-4431-8/1ac-3898fe436f37 ro quiet splash
initrd /boot/initrd.img-2.6.35-24-generic"

What do I do? I'm new to this. I researched the same kinds of error, but I can't find anything to help. If I go to command line, it doesn't recognize any of the suggested command lines I put in. (sudo, fsck, etc.)

---

### Post by MooPi on 2011-01-30
When you say use the command line your using the recovery console from grub ? If the is the case you should try this [http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by elizamach on 2011-01-30
> **MooPi said:**
> When you say use the command line your using the recovery console from grub ? If the is the case you should try this [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

I get to the list of versions of Ubuntu....there's 4 listed (2 regular, 2 recovery modes) and then 2 Memory tests listed. I press "c" to get to "command-line" which is where I get the message above.


If I select the first version of Ubuntu listed I get the following (which I've seen other people get and are offered suggestions for commands to fix it; however, my laptop isn't recognizing any of these commands):

mount: mounting /dev/disk/by-uuid/b5a79df1-0fd3-4431-81ac-3898fe436f37 on /root failed: Invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have requested /sbin/init.
No init found. Try passing init= bootarg.

BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-8in commands.

(initramfs)"

That's what I've gotten and all I've gotten for 3 days now.

I'm not sure of the 1st step to take.

I am getting my USB drive loaded with Ubuntu now to see if it will boot from that.

---

### Post by matt_symes on 2011-01-30
Hi

Do as MooPi suggested and run the script in his post. Post the results back here.

Kind regards

---

### Post by woodmaster on 2011-01-30
[http://ubuntuforums.org/showthread.php?t=1399810]("http://ubuntuforums.org/showthread.php?t=1399810")sounds like this bug:

---

### Post by elizamach on 2011-01-30
I just rebooted with the USB drive attached. Now, all I'm getting is a one line header on a black screen....
"SYSLINUX 3.82 2009-06-09 EBIOS Copyright (C) 1994-2009 Peter Anvin et al."

There is a curser blinking on the line below this line, but I cannot enter anything. 

I CAN press ESC or F10 to go into the BIOS setup. 

Should I try to go with another Linux OS? I love Ubuntu for the month I've used it.

---

### Post by elizamach on 2011-02-01
SYSLINUX 3.82 2009-06-09 EBIOS Copyright (C) 1994-2009 Peter Anvin et al.

This is all I get when I boot up now with the USB drive installed. Any ideas?

---

### Post by oldfred on 2011-02-01
Depending on the version, you may have one of these bugs.

syslinux errors help/enter works:
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779)
Delete ui in syslinux.cfg
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382)

Some prefer:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by elizamach on 2011-03-02
Ok, I have tried to do the things you all have posted and I'm getting nowhere. I tried to do the boot info script thing to no avail. My laptop does nothing. So, I'm trying to run a LiveCD from my desktop to do the bootinfoscript thing. I have gathered that I didn't burn my cd correctly because of the file images not being there like displayed on another page on here. 

Truth is I have NO idea what to do....even when you tell me to do something I'm clueless. I mean I can feel my way around a computer (I got my laptop to run Ubuntu in the first place from a LiveUSB. I can't use that usb anymore).....what to do?

Should I give up? I want to throw the thing in the trash, but then I don't, because I had it working.....and it quit.

:confused:

---

### Post by Rockcarver on 2011-03-02
Eliza, I am also a new user feeling my way through the maze. Have had not the exact same, but similar problem. Was running Ubuntu version 9.10 (Karmic Koala, they call it) installed within Windows (wubi installation). I had to reinstall it several times because of instability: disappearing functions, then total crash, similar to yours. Apparently Windows nibbles away at the Ubuntu files everytime a checkdisk is run, eventually resulting in a partial or total failure. 

Basic fact: every new release of Ubuntu contains new bugs, so sometimes it is better to use an older version for which some of the bugs have been dealt with.

So, question to you: Were you running Ubuntu as the only operating system, or was it with Windows? And what version of Ubuntu  were you running?

---

### Post by elizamach on 2011-03-02
> **Rockcarver said:**
> Eliza, I am also a new user feeling my way through the maze. Have had not the exact same, but similar problem. Was running Ubuntu version 9.10 (Karmic Koala, they call it) installed within Windows (wubi installation). I had to reinstall it several times because of instability: disappearing functions, then total crash, similar to yours. Apparently Windows nibbles away at the Ubuntu files everytime a checkdisk is run, eventually resulting in a partial or total failure. 

Basic fact: every new release of Ubuntu contains new bugs, so sometimes it is better to use an older version for which some of the bugs have been dealt with.

So, question to you: Were you running Ubuntu as the only operating system, or was it with Windows? And what version of Ubuntu  were you running?
I was using Ubuntu on its own. My laptop had been worked on and someone installed a "copy" of Windows and it deactivated itself after a certain amount of time because it had already been activated on another computer. So, I just did a full install of  Ubuntu on my laptop and it worked! I was so happy. But started freezing and giving problems and then the crash. It was the latest version. 10.10 I guess?

---

