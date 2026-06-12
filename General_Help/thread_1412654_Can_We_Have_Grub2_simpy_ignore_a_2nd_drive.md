---
title: "Can We Have Grub2 simpy ignore a 2nd drive?"
date: 2010-02-21
forum: General Help
---

### Post by bill516 on 2010-02-21
I have searched for what seemed like relevant posts, but I'm afraid I did not find one.

Here's the situation.  I am a laptop user with Ubuntu 9.10/Grub2 on sda.  A second partition on sda is a "documents" partition which is mounted through /etc/fstab to my user Home.  That way if I upgrade my Ubuntu distribution my documents or files are not disturbed.  From time-to-time I might mount a second Linux here on sda free space, though there is not one at the moment.  This all works very nicely.  Darned nice system in fact.  Kudos to the team!

I also have a grub2 Linux on an external drive.  I intend to travel with this drive when it is not convenient to haul my laptop.  I can "borrow" a host computer where I visit (mostly a family of Windows mavens) and run my Linux from the external drive.

The point:  This external drive will not always be running from the same host computer, so I do not want the Grub2 on it to be finding and categorizing operating systems (or swap files!) from sda either when it is installed or when I do update-grub.  I would like my sdb grub2 to catalog only systems on sdb.

Next point:  I do want to put other Linux distros on this extrnal drive as well, so I will want update-grub to search and catalog sdb.  How do I keep it from searching and cataloging sda?

I know that I cannot directly edit grub.cfg if sda listings show up, so what would I edit if I had to do something like that to solve this problem?

With external drives being so popular I assume somebody much smarter than I am has figured this out.  Your help is very much appreciated!

---

### Post by ajgreeny on 2010-02-21
If you run ubuntu from the external drive, it will use the grub menu, etc etc on that disk, which will point to all the grub2 config files also on that drive.  As long as the config files point to disks using their UUIDs, there should be no problem.

To stop the update-grub command finding other OSs you will need to remove the execute permissions from the **30_os-prober** file in /etc/grub.d.  I am not sure. however, if you are able to stop the system finding other OSs on your internal disks, but allow it to find them on the external disk, as the same 30_os-prober file searches all disks, not just the one it is sitting on.

---

### Post by meierfra. on 2010-02-21
This is a little bit of a hack, but should work:


```
gksudo gedit /etc/grub.d/30_os-prober
```

Look for the line

```
OSPROBED="`os-prober  | tr ' ' '^' | paste -s -d ' '`"
```

(should be line #76)

Change it to

```
OSPROBED="`os-prober [COLOR="Red"]| grep /dev/sdb [/COLOR]| tr ' ' '^' | paste -s -d ' '`"
```

Look for the line 

 ```
 LINUXPROBED="`linux-boot-prober ${DEVICE} 2> /dev/null |  tr ' ' '^' | paste -s -d ' '`"
```

(should be line 121) and change it to

  ```
LINUXPROBED="`linux-boot-prober ${DEVICE} 2> /dev/null [COLOR="Red"]|grep /dev/sdb[/COLOR]|  tr ' ' '^' | paste -s -d ' '`"
```

Save the file.

Run "sudo update-grub" to test it.

---

### Post by bill516 on 2010-02-21
beautiful and thanks so much to both of you.  I'll try to do what meierfra suggests and report back.  YIKES!! A HACK!!

courage Bill, courage ...........

---

### Post by bill516 on 2010-02-22
> **ajgreeny said:**
> If you run ubuntu from the external drive, it will use the grub menu, etc etc on that disk, which will point to all the grub2 config files also on that drive.  As long as the config files point to disks using their UUIDs, there should be no problem.

To stop the update-grub command finding other OSs you will need to remove the execute permissions from the **30_os-prober** file in /etc/grub.d.  I am not sure. however, if you are able to stop the system finding other OSs on your internal disks, but allow it to find them on the external disk, as the same 30_os-prober file searches all disks, not just the one it is sitting on.

OK, if a person is going to put a single distro on an external jump-drive that will be used on mutiple computers then ajgreeny's suggestion works beautifully.  This idea is in [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) but  was not certain just how it worked.  So my thanks to ajgreeny!

Now we'll try meierfra's more elaborate solution.  Reporting ack before too long, I hope.

---

### Post by bill516 on 2010-02-22
Here are the results of the meierfra solution.  Notice that it did not work, since it still listed Ubuntu 9.10 on sda, which is exactly what we do not want it to do.

First, to get ready for this experiment I copied meierfra's proposed solution to a gedit document so that we would not risk losing his text.

Then I copied the original 30_OS-prober to 30_OS-prober.2222010.  This should allow an easy return back to the original 30_OS-prober if we need to do that.

Next we used meierfra's opening line to get OS_prober in a root-mode gedit.  Note there is a mis-spelling on this first line.  "proper" needs to be changed to "prober".  Once done away we go.

then we made the changes suggested by meierfra.

> At line 72:

OSPROBED="`os-prober | grep /dev/sdb | tr ' ' '^' | paste -s -d ' '`"

At line 121:

LINUXPROBED="`linux-boot-prober ${DEVICE} 2> /dev/null |grep /dev/sdb| tr ' ' '^' | paste -s -d ' '`"

Next, we ran

> sudo update-grub

This returned:

> Generating grub.cfg ...
Found Debian background: linuxmint.png
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 9.10 (9.10) on /dev/sda1
Found PCLinuxOS release 2010 (PCLinuxOS) for i586 on /dev/sdb1
done


We have an entry for Ubuntu 9.10 on sda1, which is exactly what we do not want.

Sadly I do not understand scripting well enough to make the small change that meierfra's solution needs.

---

### Post by meierfra. on 2010-02-22
> 
[QUOTE]Found Ubuntu 9.10 (9.10) on /dev/sda1
We have an entry for Ubuntu 9.10 on sda1, which is exactly what we do not want.[/QUOTE]
Do your really have an entry for  "Ubuntu 9.10 (9.10) on /dev/sda1" on the grub menu?
 My hack does not prevent "update-grub" from finding OS's on /dev/sda, but it should prevents  "update-grub" from including whose OS's on the grub menu.   Could you post the content of "/boot/grub/grub.cfg"?

---

### Post by bill516 on 2010-02-23
OK, here is the /boot/grub/grub.cfg as requested by meierfra:

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,7)
search --no-floppy --fs-uuid --set d0e21e7e-a96d-45b2-ba8d-c6555b76fcbf
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1600x1024
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_mint_theme ###
insmod ext2
set root=(hd1,7)
search --no-floppy --fs-uuid --set d0e21e7e-a96d-45b2-ba8d-c6555b76fcbf
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Linux Mint 8 Helena, linux 2.6.31-14-generic (/dev/sdb7)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,7)
	search --no-floppy --fs-uuid --set d0e21e7e-a96d-45b2-ba8d-c6555b76fcbf
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=d0e21e7e-a96d-45b2-ba8d-c6555b76fcbf ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Linux Mint 8 Helena, linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,7)
	search --no-floppy --fs-uuid --set d0e21e7e-a96d-45b2-ba8d-c6555b76fcbf
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=d0e21e7e-a96d-45b2-ba8d-c6555b76fcbf ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "linux (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set bf1a1eaf-2ff4-4aa4-9b8a-6b6d21f6afaf
	linux /boot/vmlinuz BOOT_IMAGE=linux root=LABEL=PCLOS/ acpi=on resume=UUID=033ff50b-41d1-4156-b57f-9a071561fd2e splash=silent vga=788
	initrd (hd0,0)/boot/initrd.img
}
menuentry "linux-nonfb (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set bf1a1eaf-2ff4-4aa4-9b8a-6b6d21f6afaf
	linux /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=LABEL=PCLOS/ acpi=on resume=UUID=033ff50b-41d1-4156-b57f-9a071561fd2e
	initrd (hd0,0)/boot/initrd.img
}
menuentry "failsafe (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set bf1a1eaf-2ff4-4aa4-9b8a-6b6d21f6afaf
	linux /boot/vmlinuz BOOT_IMAGE=failsafe root=LABEL=PCLOS/ failsafe acpi=on
	initrd (hd0,0)/boot/initrd.img
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_os-prober2222010 ###
menuentry "Ubuntu, Linux 2.6.31-19-generic (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set bfde5bbd-019f-465a-85df-52753e573b4e
	linux /boot/vmlinuz-2.6.31-19-generic root=UUID=bfde5bbd-019f-465a-85df-52753e573b4e ro quiet splash
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set bfde5bbd-019f-465a-85df-52753e573b4e
	linux /boot/vmlinuz-2.6.31-19-generic root=UUID=bfde5bbd-019f-465a-85df-52753e573b4e ro single
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set bfde5bbd-019f-465a-85df-52753e573b4e
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=bfde5bbd-019f-465a-85df-52753e573b4e ro quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set bfde5bbd-019f-465a-85df-52753e573b4e
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=bfde5bbd-019f-465a-85df-52753e573b4e ro single
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "linux (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set bf1a1eaf-2ff4-4aa4-9b8a-6b6d21f6afaf
	linux /boot/vmlinuz BOOT_IMAGE=linux root=LABEL=PCLOS/ acpi=on resume=UUID=033ff50b-41d1-4156-b57f-9a071561fd2e splash=silent vga=788
	initrd (hd0,0)/boot/initrd.img
}
menuentry "linux-nonfb (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set bf1a1eaf-2ff4-4aa4-9b8a-6b6d21f6afaf
	linux /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=LABEL=PCLOS/ acpi=on resume=UUID=033ff50b-41d1-4156-b57f-9a071561fd2e
	initrd (hd0,0)/boot/initrd.img
}
menuentry "failsafe (on /dev/sdb1)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set bf1a1eaf-2ff4-4aa4-9b8a-6b6d21f6afaf
	linux /boot/vmlinuz BOOT_IMAGE=failsafe root=LABEL=PCLOS/ failsafe acpi=on
	initrd (hd0,0)/boot/initrd.img
}
### END /etc/grub.d/30_os-prober2222010 ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

---

### Post by meierfra. on 2010-02-23
> ### BEGIN /etc/grub.d[COLOR="Red"]/30_os-prober2222010[/COLOR] ###
menuentry "Ubuntu, Linux 2.6.31-19-generic (on [COLOR="Red"]/dev/sda1[/COLOR])" {
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set bfde5bbd-019f-465a-85df-52753e573b4e
linux /boot/vmlinuz-2.6.31-19-generic root=UUID=bfde5bbd-019f-465a-85df-52753e573b4e ro quiet splash
initrd /boot/initrd.img-2.6.31-19-generic
}

you still have the OS from  /dev/sda1 on your Grub menu, but it was created by  the backup of 30_os-prober.

So disable the backup via:

```
sudo chmod -x /etc/grub.d/30_os-prober2222010
```

Then run "sudo update-grub"

and you will have only the OS's from /dev/sdb on the Grub menu.

---

### Post by bill516 on 2010-02-23
Yes Sir that works and thank you so much!  :D

For other readers:  "sudo update--grub"  should be "sudo update-grub"

Question:  Surely I am not the only person who is going to travel with an external drive from which I boot my preferred system(s).  How hard might it be to modify OS-prober so that the user gets a menu that specifies which drives are to be searched?

Suppose I have three drives, hd0, 1 and 2.  The default might be that all three drives are checked on the menu.  If I want to exclude one or two I simply clear that checkmark.

Would such a thing be possible and desirable?

---

### Post by leorolla on 2010-12-27
From the link [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) I found that
```
echo "GRUB_DISABLE_OS_PROBER=true" | sudo tee -a /etc/default/grub

```does what you are looking for.

---

### Post by imwithid on 2011-08-08
> **meierfra. said:**
> you still have the OS from  /dev/sda1 on your Grub menu, but it was created by  the backup of 30_os-prober.

So disable the backup via:

```
sudo chmod -x /etc/grub.d/30_os-prober2222010
```

Then run "sudo update-grub"

and you will have only the OS's from /dev/sdb on the Grub menu.

Excellent solution. I was hesitant to attempt this until I was able to find someone to confirm. Simple, effective and easy to reverse.

I have multiple drives coming in and out of my system and this the only way to go.

---

### Post by masuch on 2012-04-29
thank you so much for this posts.

Is there any way how to update-grub ignoring usb drives (except get them out of usb port :-) ?

thanks for any clue.

did not find any relevant information on [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Martin

---

