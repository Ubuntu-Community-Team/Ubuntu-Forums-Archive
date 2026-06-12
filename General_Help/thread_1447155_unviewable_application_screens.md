---
title: "unviewable application screens"
date: 2010-04-05
forum: General Help
---

### Post by a_hippie on 2010-04-05
This is odd, but some applications will not "show up" on my Karmic laptop.  I will attach a screen shot of the application "system monitor" to demonstrate the problem.  Almost everything else works, but this app and a ham radio application (qsstv) that just come up as lines.  I know that there is the "x" at the very top right and if I click there, the app is shut down.  

What is going on?  Originally, when I first installed Karmic on here, most of the apps looked like that, but I turned off the themes and visual effects which seemed to solve all but this problem.

Any tips/hints very welcome.  I googled a while but I don't even know how to adequately describe the problem here!

Thank you,

---

### Post by NightwishFan on 2010-04-05
So turning off Desktop Effects solves the problem? Please tell me what the model of your graphics card is.

---

### Post by a_hippie on 2010-04-05
> **NightwishFan said:**
> So turning off Desktop Effects solves the problem? Please tell me what the model of your graphics card is.

It solved MOST of the problems.  The graphics is Intel and it's an IBM x31 thinkpad with 2gb memory.  The screen shot shows what happens when I launch a few effected applications.

thank you,

---

### Post by NightwishFan on 2010-04-05
I see, perhaps report this as a bug. For now try:

[LIST=1]
[*]With the use of the arrow keys, highlight the title of your choice you want to edit (the first Ubuntu entry should be ok) and press "e" to go to the entry editor interface. You will now see the boot entries for the title you selected.
[*]Highlight, again with the use of the arrow keys, the line that say "kernel" (it might say linux not sure) and press "end" to go to the end of the line.
[*]Add, without the quotes " vga=normal nomodeset" and press the enter key to go out of edit mode.
[*]Press the ctrl+X to boot your system.
[/LIST]

---

### Post by a_hippie on 2010-04-05
> **NightwishFan said:**
> I see, perhaps report this as a bug. For now try:

[LIST=1]
[*]With the use of the arrow keys, highlight the title of your choice you want to edit (the first Ubuntu entry should be ok) and press "e" to go to the entry editor interface. You will now see the boot entries for the title you selected.
[*]Highlight, again with the use of the arrow keys, the line that say "kernel" (it might say linux not sure) and press "end" to go to the end of the line.
[*]Add, without the quotes " vga=normal nomodeset" and press the enter key to go out of edit mode.
[*]Press the ctrl+X to boot your system.
[/LIST]

NightwishFan:

I think you must have skipped a dozen steps or something.  What does highlight the title of my choice mean?  What application will reboot the system with a "ctrl X"?  

Are you talking about editing grub, or some gnome config file?  

thank you,

---

### Post by NightwishFan on 2010-04-05
I am sorry, the beginning must have been deleted. Doh!

Reboot, and when you are prompted to select Ubuntu, press E to edit the boot entry, and you will see what I mean. If you do not get a choice to boot Ubuntu, hold in the shift key while booting. Then do the above.

---

### Post by a_hippie on 2010-04-05
Wow, failure.  BTW, those directions do not work for a karmic install.  Perhaps they would work with the upcoming release.

I used bash (sudo to root) to use vi to make the change:

(this text extracted from /boot/grub/grub.cfg since menu.1st doesn't exist)

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        set quiet=1
        insmod ext2
        set root=(hd0,5)
        search --no-floppy --fs-uuid --set 3c58632b-6680-4b6d-a07c-327b32ec2518
        linux   /boot/vmlinuz-2.6.31-20-generic root=UUID=3c58632b-6680-4b6d-a07c-327b32ec2518 ro   quiet splash vga=normal nomodeset
        initrd  /boot/initrd.img-2.6.31-20-generic
}

So now going to change it back.  BTW, I had to change permission (add write) then change it back to readonly.

Anyway, this problem looks very much like some kind of windowlibrary is broken.  Qsstv uses qt and I don't know what "system monitor" requires, but I'd guess it depends on gnome.  Very odd.

I just edited this post and added two more screen shots.  In the first screenshot I shrank Firefox, opened gnome terminal and then launched "qsstv".  Note that only some applications have broken windows.  Gnome terminal, Firefox and most other applications work fine.  In the second screenshot I opened and maximized gnome terminal and then launched gnome-system-monitor, and that is the broken application window you see in the middle of the screen.  I hope this helps.

thank you,

---

### Post by a_hippie on 2010-04-18
this is interesting.  I just downloaded and installed picasa and bygolly it also is unreadable.  Just get hashmarks in the dialog window!  I sure wish someone with more clue to fill me in on what's happening!

thank you!

regards,

---

### Post by ed-koala on 2010-04-18
Just a thought.  Go to System - Administration - Hardware Drivers and see if there isn't some recommended video driver.  Definitely *sounds* like a video driver problem of some sort to me.

---

