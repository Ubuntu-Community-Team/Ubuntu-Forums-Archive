---
title: "[GRUB] Installed kde over gnome in ubuntu, lost its conf, can't boot, help restore it"
date: 2009-10-10
forum: General Help
---

### Post by Miki800 on 2009-10-10
I installed ubuntu via wubi, booted into it.
got into a live-cd desktop on the ubuntu wubi image that was just booted from the hard disk with the "Install Ubuntu 9.10" installation link on it.
completed the installation, restarted and it was over.


everything worked perfectly, this is the most stable release I've experienced as a simple user yet.

then I tried to install kde: kde-desktop and kdebase

so I did via synaptic and from time to time windows of stuff to configure popped up.

eventually I saw a grub configuration window popping up.
I DID NOT want to change ANYTHING about the current working configuration that I had in grub, so the thing I thought was the least damaging to do was to de-select any and all (hda) lines I had in the grub configuration window.

and that was because I had numerous horrible experiences with grub in the past.

plus - everyone knows - if it works don't try to fix it (stupid kde installation!!  )

this had caused the destruction of my current grub configuration.

each reboot (if I select Ubuntu from ntldr) I get a grub prompt window with commands I know nothing to do with about.

like:

"linux ..."
"initrd ..."
and then I guess you need to write "boot"


an ancient backup of a 'grub.cnf' file I have that's from the 8.04 era has this:



title Ubuntu 8.04.1, kernel 2.6.24-18-generic
root (hd1,5)
kernel /boot/vmlinuz-2.6.24-18-generic root=UUID=2cb4037e-ed06-4be8-b295-43fa621d7f33 ro quiet splash
initrd /boot/initrd.img-2.6.24-18-generic


I have no kernel command in the current grub, so I suppose its replacement is now the command 'linux'
also I noticed that I had no reason to declare the wubi image file as the root since it was already the current situation.

the only thing I had to do by myself was 'kernel /boot/vmlinuz-something something' (which is now called 'linux')
and 'initrd /boot/initrd-something something'

and afterward complete the grub booting process by typing the command 'boot' with no params


so that was exactly what I did, the only problem is that it caused a reboot of the computer.

so right now I am clue-less and powerless to restore the perfectly good working grub configuration I had before kde installation destroyed it :(


please help me

[edit]
I've just used andLinux to mount the wubi image and see whats wrong with the whole grub boot process
it seems that there is NOTHING wrong with it
as the matter of fact I believe it hasn't changed since I started booting wubi for the first time.

so the problem is that right now I have another boot loader running, which forces me to specify my hd specs:

hda1 = C:\
hda5 = D:\
hda6 = E:\
( I hope I got that right )

E:\ubuntu\disks\root.disk = the ubuntu image.

I think that from some reason the used grub boot loader has ceased to be the one inside root.disk
and now somehow from some reason it is something else, I have no idea how to solve this issue or no idea if my assumption is correct
[/edit]

[edit2]
I have under the root path of the wubi image the following files:
initrd.img
initrd.img.old
vmlinuz
vmlinuz.old

should I skip the old ones with the current ones to see if that fixes everything?
should I not because it will be harmful?

help :)
[/edit2]

---

### Post by quixote on 2009-10-11
I'm confused about what your situation is, partly because I haven't used wubi, so somebody else will have a better answer for you.  I just wanted to say that I don't think you need to get too worried.  Everything is still there, it just needs to get pointed at the right drives / partitions again.  

Also, don't worry about skipping the .old files.  The system isn't seeing those anyway.  That's what appending that .old extension does.  They're just kept as a fallback, in case the new ones have a problem, the old ones can be renamed to the active form, without the .old

---

### Post by Miki800 on 2009-10-13
I figured that much by myself, after manually booting from those files, renaming them to the supposibly active form, trying to let grup do it's magic by recognizing them by itself after another boot - grub FAIL (ed).

so now I have to (everytime) manually boot ubuntu which is really a pain.
I've noticed that the menu/grub.cfg file has the right parameters in it and grub just refuses to load it, stupid grub!

---

### Post by quixote on 2009-10-13
>I've noticed that the menu/grub.cfg file has the right parameters in it

You don't have Grub2 do you?  Grub2 uses a grub.cfg file.  Earlier Grub has it's configuration in a file called "menu.lst" (that's .lst as in "list").  Let's first make sure we're both talking about the same thing, because configuration for Grub2 is handled very differently.

It should say which version you have on boot up.  Or you can open a terminal and type "grub --version"

---

### Post by Miki800 on 2009-10-22
I'm in the grub-shell thingy where I can use commands like
ls
cat
set
root
boot
linux
initrd

etc..

I DO NOT have a command called grub and I (obviously) most definitely can not preform grub --version
tried - it failed saying something like no such thing as 'grub' or something like that, didn't though of writing the error down at the time.


so,.............
I CAN boot manually,
the only REAL help I need right now is telling me how to force grub to acknowledge a specific boot script to use each time so I do not have to boot manually anymore?
that boot script can be anywhere, the wubi image file, one of my windows ntfs partitions... I do not care :)

---

### Post by quixote on 2009-10-22
What does the prompt look like:  "grub>"  or is the last character "#"?  Or is it maybe "$"

All of those are very different command line terminals, and it's hard to suggest anything without knowing what you're looking at. 

When you boot, as you say, "manually," which steps, line by line, do you use?

If you can boot into ubuntu, any way that works, type the following at the command prompt (Assuming the prompt is not "grub>".  It won't work then.)```
ls /boot/grub/
```Is there such a directory?  Is "menu.lst" in that directory?  Not "menu.cfg."  "Menu.lst"

---

### Post by Miki800 on 2009-10-23
> **quixote said:**
> What does the prompt look like:  "grub>"  or is the last character "#"?  Or is it maybe "$"

All of those are very different command line terminals, and it's hard to suggest anything without knowing what you're looking at. 

When you boot, as you say, "manually," which steps, line by line, do you use?

If you can boot into ubuntu, any way that works, type the following at the command prompt (Assuming the prompt is not "grub>".  It won't work then.)```
ls /boot/grub/
```Is there such a directory?  Is "menu.lst" in that directory?  Not "menu.cfg."  "Menu.lst"
I used andLinux to mount the wubi image from windows and extracted the wubi ext3 image contents of the boot folder.
I have the following relevant grub.cfg file:

> 
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
load_env
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
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

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.31-13-generic" {
	insmod ntfs
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set bcfa2780ce0edca1
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-13-generic root=/dev/sda6 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.31-13-generic
}
menuentry "Ubuntu, Linux 2.6.31-13-generic (recovery mode)" {
	insmod ntfs
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set bcfa2780ce0edca1
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-13-generic root=/dev/sda6 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.31-13-generic
}
menuentry "Ubuntu, Linux 2.6.31-11-generic" {
	insmod ntfs
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set bcfa2780ce0edca1
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-11-generic root=/dev/sda6 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.31-11-generic
}
menuentry "Ubuntu, Linux 2.6.31-11-generic (recovery mode)" {
	insmod ntfs
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set bcfa2780ce0edca1
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-11-generic root=/dev/sda6 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.31-11-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 14ff59b7d52f0b71
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###



what I do to boot manually is type the following lines every time:
> 
insmod ntfs
set root=(hd0,6)
search --no-floppy --fs-uuid --set bcfa2780ce0edca1
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /vmlinuz.old root=/dev/sda6 loop=/ubuntu/disks/root.disk ro quiet splash
initrd /initrd.img.old


this is the only way I found out that it'll work.

sometimes grub will freeze after I type the 80th char of the 'linux' command line
meaning after I type enough chars to fill a line instead of letting me continue to type to the next line it just freezes from time to time so I have to restart and try again.

---

### Post by quixote on 2009-10-23
You're using Grub2, which is newer faster better, but I don't know as much about it yet.

Since default=0, the first entry is the one grub tries to use:```
### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.31-13-generic" {
insmod ntfs
set root=(hd0,6)
search --no-floppy --fs-uuid --set bcfa2780ce0edca1
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux [COLOR="Red"]/boot[/COLOR]/vmlinuz[COLOR="Red"]-2.6.31-13-generic[/COLOR] root=/dev/sda6 loop=/ubuntu/disks/root.disk ro quiet splash
initrd [COLOR="Red"]/boot[/COLOR]/initrd.img[COLOR="Red"]-2.6.31-13-generic[/COLOR]
}
```

The last two lines differ (highlighted in red) from what you enter by hand:
```
linux /vmlinuz.old root=/dev/sda6 loop=/ubuntu/disks/root.disk ro quiet splash
initrd /initrd.img.old 
```

I'd be willing to bet that all you need to do is remove that extra "/boot" in the path in the last two lines above in grub.cfg.  You have the files it needs to boot in the root directory (just plain "/") and not in the /boot subdirectory.

Also, when you type in by hand, you're saying to use the .old versions, which obviously exist because they work.  Look in the / (toplevel) directory and make sure vmlinuz-2.6.31-13-generic and initrd.img-2.6.31-13-generic are actually there.  If not, when editing grub.cfg, also change those file names to the latest vmlinuz and initrd-img files you have.  Or to the .old files, if you prefer the older version or that's the only one that works.

Hopefully this will solve all the problems.  :D

---

### Post by Miki800 on 2009-10-24
> **quixote said:**
> You're using Grub2, which is newer faster better, but I don't know as much about it yet.

Since default=0, the first entry is the one grub tries to use:```
### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.31-13-generic" {
insmod ntfs
set root=(hd0,6)
search --no-floppy --fs-uuid --set bcfa2780ce0edca1
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux [COLOR="Red"]/boot[/COLOR]/vmlinuz[COLOR="Red"]-2.6.31-13-generic[/COLOR] root=/dev/sda6 loop=/ubuntu/disks/root.disk ro quiet splash
initrd [COLOR="Red"]/boot[/COLOR]/initrd.img[COLOR="Red"]-2.6.31-13-generic[/COLOR]
}
```

The last two lines differ (highlighted in red) from what you enter by hand:
```
linux /vmlinuz.old root=/dev/sda6 loop=/ubuntu/disks/root.disk ro quiet splash
initrd /initrd.img.old 
```

I'd be willing to bet that all you need to do is remove that extra "/boot" in the path in the last two lines above in grub.cfg.  You have the files it needs to boot in the root directory (just plain "/") and not in the /boot subdirectory.

Also, when you type in by hand, you're saying to use the .old versions, which obviously exist because they work.  Look in the / (toplevel) directory and make sure vmlinuz-2.6.31-13-generic and initrd.img-2.6.31-13-generic are actually there.  If not, when editing grub.cfg, also change those file names to the latest vmlinuz and initrd-img files you have.  Or to the .old files, if you prefer the older version or that's the only one that works.

Hopefully this will solve all the problems.  :D
oh, most definitely no.
I definitely know that those files exists there under /boot and under /
I tried "MANUALLY" them both, (actually all 4 of them, the 2 under /boot and the 2 under /) and only what I said worked - worked.
(thanks for trying to help though, I really do appritiate it! :) )

BUT - that has nothing to do with the problem at hand.
grub SHOULD load anyways and fail only once I select that menu option if its wrong.

if I add another menu option of the kind that works manually I bet it will not make any difference since the menu did not load in the first place as it is right now.
(if you're suggesting that even if one menu option will work - the menu will work
you can see that the menu includes the windows xp boot loading option which I'm running from right now so thats a good example why such assumption isn't true or something..)

the problem is that after I installed kde over gnome it did something to my grub preloader in a way
which prevents it from loading properly when booting

I believe theres a command to force the manual boot grub shell thingy
to "LOAD" a menu file from a path I give it, I once knew that command now forgot all about it.

anyways I think this command would give me an error message about what is wrong with the configuration file (line, colm bad keyword etc...) that prevents grub from loading it.

maybe the grub version of the kde installation is different in a way
that the grub configuration generated from the gnome grub version of the original gnome installation does not fit it.


maybe if I can restore the gnome version of grub that came with wubi when I first installed it
THAT grub will re-recognize the correct and expected syntax of that grub.cfg file and everything will "AUTOMAGICALLY" (I love that word ^_^) work again.



comments (and instructions) anyone?

---

### Post by quixote on 2009-10-25
I seem to keep misunderstanding what you're saying.  If the various choices of OS don't come up at the beginning (that's what you mean by "menu", right?) then you need to reinstall grub, by the sound of it.  There are extensive instructions for grub2 here: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

If the commands you enter manually work, but do not work once they're in the menu.cfg, then either "default" is pointing to the wrong entry, or possbily grub needs reinstalling.  Maybe somebody else has other ideas for what could be wrong.

---

