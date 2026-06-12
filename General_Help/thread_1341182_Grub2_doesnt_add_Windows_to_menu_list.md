---
title: "Grub2 doesnt add Windows to menu list"
date: 2009-11-29
forum: General Help
---

### Post by NFblaze on 2009-11-29
So, I just installed Ubuntu on the house computer, everything is great it works and all except this damned grub2 will not add Windows to my boot menu, no matter how many times I do update-grub or edit 40_custom.
I really meed it to still boot windows as this is a communal PC.

---

### Post by GepettoBR on 2009-11-29
What exactly are you adding to 40_custom?

You can add a Windows chainloader to 40_custom like this:```
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 8e0446680446537f
	chainloader +1
}
```

Making the necessary replacements for your Windows partition. I took that entry from my own grub.cfg, though it was added automatically by the 30_os-prober script. I do not believe the line starting with "search" is absolutely necessary.

---

### Post by NFblaze on 2009-11-29
```
echo "Windows Media Center XP" >&2
menuentry "Windows Media Center XP" {
insmod ntfs
set root=(hd0,1)
search --no-floppy --fs-uuid --set 1CFC033DFC0310A6
chainloader +1
} 
```

That is exactly what I have put into the 40_custom because the 30_OS prober doesnt find my Windows OS.

---

### Post by GepettoBR on 2009-11-29
What exactly is the error message you get when you try to boot from that entry?

---

### Post by NFblaze on 2009-11-29
There is no error, the grub menu just stays the exact same. It list Ubuntu, Ubuntu Recovery, Memtest, Memtest +86. It's like it's not detecting the Windows Partition

---

### Post by GepettoBR on 2009-11-29
> **NFblaze said:**
> There is no error, the grub menu just stays the exact same. It list Ubuntu, Ubuntu Recovery, Memtest, Memtest +86. It's like it's not detecting the Windows Partition

So you've added that entry to 40_custom and ran update-grub as root, but the entry doesn't even appear in the GRUB menu?

Can you post the output of running ```
sudo grub-mkconfig
``` in a terminal? Better yet, run ```
sudo grub-mkconfig > ~/Desktop/grub.txt
``` and attach the grub.txt file that will appear on your Desktop to your next post.

---

### Post by NFblaze on 2009-11-29
Ok, some new findings.

In the actual /boot/grub.cfg I can see the custom entry has been in the file this whole time.
```
[SIZE="2"]### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

echo "Windows Media Center XP" >&2
menuentry "Windows Media Center XP" {
insmod ntfs
set root=(hd0,1)
search --no-floppy --fs-uuid --set 1CFC033DFC0310A6
chainloader +1
} 
### END /etc/grub.d/40_custom ###[/SIZE]
```

Though it will not appear on the actual boot menu. Another note, I apt-get remove grub2 and rebooted and the system still rebooted into the same menu. Also, the grub.cfg file and the /etc/grub.d/ folder and it's contents were still there.

I then tried to install Grub Legacy, rebooted again and the same grub2 menu loaded up. The install was done using Ubuntu Lucid Lynx daily build iso, so it may just be an issue with the build, though I wouldnt think so.

---

### Post by GepettoBR on 2009-11-29
If the entry is in your config file but doesn't appear in the menu, the only thing I can think of is that your ""echo "Windows Media Center XP" >&2"" line is causing GRUB to ignore the remainder of the entry in grub.cfg.

That line doesn't serve any purpose that I can see. The title of the entry will be whatever is between the quotation marks in the menuentry line. perhaps if you remove the echo line and run update-grub once again (you should install grub2 again before running that command) the entry will show up.

Even if it doesn't, try booting into Windows by pressing "c" on the GRUB2 menu screen and manually typing ```
insmod ntfs
set root=(hd0,1)
chainloader +1
boot
```

This way we can see if it boots at all at least, and single out the bootloader menu as the only problem.

---

### Post by sisco311 on 2009-11-29
remove the *echo "Windows Media Center XP" >&2* from the 40_custom file. That line should not appear in the grub.cfg file.
and run:
```
sudo update-grub
```

EDIT. Sorry GepettoBR, I didn't read your post carefully. You are right.

*echo "Windows Media Center XP" >&2* should print "Windows Media Center XP" to the stdout when you run update-grub, but it seems that the command is not executed just copied to the grub.cfg file.

---

### Post by NFblaze on 2009-11-29
[quote=GepettoBR]If the entry is in your config file but doesn't appear in the menu, the only thing I can think of is that your ""echo "Windows Media Center XP" >&2"" line is causing GRUB to ignore the remainder of the entry in grub.cfg.

That line doesn't serve any purpose that I can see. The title of the entry will be whatever is between the quotation marks in the menuentry line. perhaps if you remove the echo line and run update-grub once again (you should install grub2 again before running that command) the entry will show up.

Even if it doesn't, try booting into Windows by pressing "c" on the GRUB2 menu screen and manually typing[/quote]

Thanks for your asssitance, I tried all the aformentioned before and this did not resolute the situation. I will however see if an earlier version of Ubuntu will produce the same issue. Thanks again.

---

### Post by fNNR on 2009-12-15
I have the same problem, does anyone have a solution to this problem?

---

### Post by oldfred on 2009-12-16
fNNR this thread was solved with remove the echo line in his custom windows entry. I doubt you have that.

You should start a new thread with a little more description of your system, partitions and problem. I do not think you have grub2 with 6.10, so also is it a new install or an upgrade?

---

