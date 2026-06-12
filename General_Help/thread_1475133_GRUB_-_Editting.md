---
title: "GRUB - Editting"
date: 2010-05-06
forum: General Help
---

### Post by Nelsaidi on 2010-05-06
Hey,

First of all I'm a partial noob to kubyx and using it to avoid buying windows 7 for my bloated crappy laptop with vista on it.

I'd like to edit the boot settings, currently i'm given 6 options:
kubuntu
kubuntu recovery
memtest
memtest (soemthing i cant remember)
windows recovery mode (windows vista)
windows xp embedded (Wtf is this?)

I'd like to change the names, Windows recovery mode to windows vista and if possible remove all but kubuntu standard and vista (so only two options) - vista being the default?

Thanks

---

### Post by darolu on 2010-05-06
It is possible to do all this but you may not find it that trivial; you need to edit a few system files, GRUB2 works different than GRUB Legacy (GRUB 1), first read this link so you can have a better understanding of how it works:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

First, take the recovery options out of your grub by editing the /etc/default/grub file with your favourite text editor, for this example I'll use Kate (the default text editor for Kubuntu), open a terminal and type:
```
$ sudo kate /etc/default/grub
```
Search this line (should be by the end) and uncomment it (removing the #):
```
# Uncomment to disable generation of recovery mode menu entries
GRUB_DISABLE_LINUX_RECOVERY="true"
```
Save the file and run "sudo update-grub" to apply changes (you can do it one time after all changes are made too).
After that, lets kill the memtest entries, to do it we need to take the execution permission off the memtest script under /etc/grub.d/, in your terminal run:
```
$ sudo chmod -x /etc/grub.d/20_memtest86+
```
Again, you can apply changes with "sudo update-grub", finally to eliminate the windows entries and customize their menuentry line you'll have to disable the os-prober script and create custom entries for them; first we need to create the custom entries, we write them in the /etc/grub.d/40_custom file, but first we need to learn what to type in it, open the /boot/grub/grub.cfg file and copy the windows entry you want to modify, do **not** use sudo this time, that way you won't be able to write and (potentially) screw the boot loader:
```
$ kate /boot/grub/grub.cfg
```
Look for your Windows entry, it should be after the ### /etc/grub.d/30_os-prober ## line, for example:
```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7e204c84204c44fd
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###
```
Copy the entry you want to use, in your case the "Windows recovery mode (windows vista)", make sure you copy the entire block, from "menuentry" to the final "}", now open your 40_custom file (with sudo now) and paste the Windows entry text:
```
$ sudo kate /etc/grub.d/40_custom
```
You are going to edit the menuentry string **only** to whatever you want, for example:
```
menuentry "**Winbugs Vista**" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7e204c84204c44fd
	drivemap -s (hd0) ${root}
	chainloader +1
}
```
Save the file and run "sudo update-grub". Reboot and test your custom entry, if it works proceed to the next step, elminating the extra windows entry (disabling os-prober script).

If your custom entry worked, remove the execution permission to the /etc/grub.d/30_os-prober entry with:
```
$ sudo chmod -x /etc/grub.d/30_os-prober
```
And finally run "sudo update-grub".

---

