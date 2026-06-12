---
title: "dual boot w/xp cannot change order"
date: 2011-08-18
forum: General Help
---

### Post by sgrad on 2011-08-18
I installed Ubuntu 11.04 as a dual boot system. I am given 5 choices with XP choice 5. Unless I highlight it I will boot into Ubuntu. I used the startup manager, and indicated that XP should be the default OS. Nothing changed. I tried the PySDM storage device manager which lists the partitions, but does not allow me to make changes. 
Any body tell what I am doing wrong or how to fix this. 
I am brand new to Ubuntu so this all very new and foreign, so any suggestions please be verbose.

---

### Post by angry_johnnie on 2011-08-18
startupmanager was great for grub legacy.  grub2 however, is a tad more complicated.

read [this]("http://ubuntuforums.org/showthread.php?t=1195275") for further info on it.

the quick and dirty way to do it would be to change the permissions of your grub.cfg file.

```
sudo chmod a+w /boot/grub/grub.cfg
```

then edit it:

```
gksu gedit /boot/grub/grub.cfg
```

and then just cut your windows menuentry and paste it as the first one.

you'd have something like this:

```
### BEGIN /etc/grub.d/10_linux ###

menuentry "windows" {
	insmod ntfs
	set root='(hdx,x)'
	search --no-floppy --fs-uuid --set somethingsomething
	drivemap -s (hdx) ${root}
	chainloader +1
}

menuentry 'ubuntu' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hdx,x)'
	search --no-floppy --fs-uuid --set something something
	linux	/boot/vmlinuz-2.6.x-x-generic root=UUID=something ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
	initrd	/boot/initrd.img-2.6.x-x-generic
}

and so on...
```

and then save it, and finally revert permissions.

```
sudo chmod a-w /boot/grub/grub.cfg
```


of course this is just an example, your list will look different, but for the most part, it should do the trick.  just be careful with what you edit.  you're just going for the menuentries, so be careful not to bork it, if you decide you want to change somehting else.

the downside to editing grub.cfg the quick and dirty way, is that every time your system runs update-grub (for example, every time a new kernel is installed) it will revert it back to the way it was, and you'd have to go back in there, and change your lines.

in order to avoid update-grub from messing it up every time, you'd need to read the whole grub2 guide and figure it out somehow.

---

### Post by Mark Phelps on 2011-08-18
While I agree that editing grub.cfg is a quick way to test out changes, I strongly disagree with using it to correct boot issues for long-term use.

The file you SHOULD edit is /etc/default/grub.  You will find a line in there with a DEFAULT=0 statement.  Look through the boot stanzas in your grub.cfg file and change that number ZERO to the number of your stanza.  Since they count from ZERO, if XP is stanza #5 (for example), change that ZERO to a 4.  Save the file.

Then, run "sudo update-grub".  That will regenerate the grub.cfg file.

Since kernel upgrades have historically changed the number of entries in the GRUB menu, a better solution is to replace the "4" with the text string associated with that GRUB stanza.

For example, let's say that stanza says "Windows XP (Loader) on sda3".  Then replace the "4" with this last string, including the double-quote marks (because it has embedded blanks).  Then save and do the sudo command again.

Now, even if you add or remove kernel entries to GRUB, the default will stay the same.

---

