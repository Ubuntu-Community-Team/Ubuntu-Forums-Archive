---
title: "Need to add Grub2 kernel option"
date: 2010-01-10
forum: General Help
---

### Post by VideoRoy on 2010-01-10
I have been reading for hours and just do not get how to do this simple task.  I need to add a couple of kernel options to the 3rd menu item that shows in my grub.cfg list.  I understand which files to edit (not grub.cfg) and run the updater.

If I look in /etc/default/grub I cannot figure out how to add a kernal parameter unless it is the default.

So basically I want to change the equivilent of this line below:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

but for a kernel menu item that is not the default.

I am usually a quick learner but after reading all the guides it is just escaping me and I cannot find a similar example.

Any help would be appreciated.

---

### Post by ajgreeny on 2010-01-10
I believe you will need to edit the file **40_custom** and add the appropriate entry to your required OS with the boot parameters you want.  My **40_custom** file, already edited just to show how to do it in future is shown below, but mine is not executable as I do not have anything custom to boot.

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

#Below is an example of the required format for an entry to add to the grub menu.
#To use it, add similar info for any new OS, without the # at start of lines, and run update-grub command.

#menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic"{
#set root=(hd0,2)
#linux/boot/vmlinuz-2.6.28-15-generic root=UUID=10ec6342-7b3f-425c-8655-c637bb65ae72 ro quiet splash 
#initrd        /boot/initrd.img-2.6.28-15-generic
#}

```
You can add your parameters to the entry as you would in legacy grub, then if you want that to be the default entry at the top of the menu, just rename the file **09_custom** and it will be run before **10_linux**

---

### Post by VideoRoy on 2010-01-10
ajgreeny,
Thanks for the help! I will give this a try.

One question, if I do not make any other changes to other files, I assume I will end up with a duplicate entry for that particular kernel entry?

Grub2 looks very configurable, but very frustrating to learn when you are in a hurry and have a lot of other work to do!:sad:

---

### Post by ajgreeny on 2010-01-10
> **VideoRoy said:**
> ajgreeny,
Thanks for the help! I will give this a try.

One question, if I do not make any other changes to other files, I assume I will end up with a duplicate entry for that particular kernel entry?

Grub2 looks very configurable, but very frustrating to learn when you are in a hurry and have a lot of other work to do!:sad:
No problem, I hope it works.

To answer your question, yes you will get duplicates, I think, unless you need the same boot parameter for all your linux OSs, when you can add everything you need to the 09_custom file and make the 10_linux file non executable.  In fact you could do that anyway, even for the linux OSs which don't need the boot parameter, but the grub.cfg will not then be updated with new kernels automatically after any are installed by updates.

Yes I agree, grub2 does seem to be very configurable, but as I have not yet learned my way around the methods that it uses, these suggestions are at your own risk.  I do know that the custom file I made works as I did try that with success.  Thank goodness for live CDs and the ability to edit files without even using the OS on which you need to make the edit.

---

### Post by VideoRoy on 2010-01-10
Ok, spent waaaay more time on this than I wanted but now I am expert ;) (yeah right).

ajgreeny put me on the right track and even though I read a bunch it was just not clicking.  I ended up making a 06_custom file (actually found this name as an example after I did it!) and I had to put a bunch of extra lines in there to get my realtime kernel loading correctly.  Also by making this 06_custom, the menu entry is now first in the list an is the default if I am not there to hit enter.

> ### BEGIN /etc/grub.d/06_custom ###

menuentry "Ubuntu 9.10, kernel 2.6.31-9-rt (nosmp acpi=off)"{
  recordfail=1
  if [ -n  ]; then save_env recordfail; fi
  insmod ext2
  set root=(hd0,1)
  search --no-floppy --fs-uuid --set e12ad3fc-6403-47e9-8396-d21537da42dc
  linux    /boot/vmlinuz-2.6.31-9-rt root=UUID=e12ad3fc-6403-47e9-8396-d21537da42dc ro   quiet splash nosmp acpi=off
    initrd    /boot/initrd.img-2.6.31-9-rt
}
### END /etc/grub.d/06_custom ###Also I finally get it.  update-grub is concatenating a bunch of files together that are a script file.  Each custom file needs to be executable which is why there is a [COLOR=Blue]tail[/COLOR] command at the top of 40_custom as an example.  The problem with tail is that it is going to put it at the end of the script file so I had to make adjustments and remember my 20 year old scripting writing learnings.

Thanks for the help.

---

