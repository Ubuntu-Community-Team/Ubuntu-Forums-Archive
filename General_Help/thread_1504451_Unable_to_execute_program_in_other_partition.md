---
title: "Unable to execute program in other partition"
date: 2010-06-08
forum: General Help
---

### Post by ranjithnair on 2010-06-08
I hav added following line in /etc/fstab to automount during startup now the problem is [COLOR="Red"]I hav a program in one of the partitions i am not able to execute it can somebody tell me how to make it executable[/COLOR],.......
[B]
/dev/sda4 /media/Movies vfat user,fmask=0111,dmask=0000 0 0

/dev/sda6 /media/Songs ntfs defaults 0 0

/dev/sda5 /media/Software vfat user,fmask=0111,dmask=0000 0 0

/dev/sda2 /media/WINXP ntfs defaults 0 0[/B]

---

### Post by BoneKracker on 2010-06-08
> **ranjithnair said:**
> I hav a program in one of the partitions i am not able to execute

Which partition is the file in?  /dev/sda5?

You have applied an fmask of 0111 to two partitions.  This makes files in those directories not executable unless you change their file mode.  This is likely the cause of your problem.  If you, you would change the file's mode in nautilus, making it executable.  If the file is owned by root you will have to do this in the terminal using the 'sudo chmod <options> <filename>' command (see the chmod man page).


Also, as a separate issue, you would be better off using "UUID=" or "LABEL=" entries for your devices, rather than "/dev/sdX" entries.
Ubuntu seems to lack the ability to persistently apply "/dev/sdX" type names to devices.

Also, if you used fmask 01111 for security reasons, a better way to make everything non-executable is to put noexec in the fstab options.

Also, I'm not sure what the purpose of your Software directory is, but you might want to read this:
[http://www.pathname.com/fhs/](http://www.pathname.com/fhs/)

---

