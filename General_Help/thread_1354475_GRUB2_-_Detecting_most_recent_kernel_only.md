---
title: "GRUB2 - Detecting most recent kernel only"
date: 2009-12-13
forum: General Help
---

### Post by mclark1129 on 2009-12-13
Hello,

After a recent update to my Linux kernel (2.6.31-14 to -16) GRUB now displays two sets of menu entries for each kernel I have installed.  After some research I was able to figure out that the 10_Linux GRUB script automatically generates the menu entries based on the kernels it detects on the machine.  Ideally I'd like to keep the automatic generation feature of the script, although I'd like to limit the script to generating an entry for only the most up to date kernel that is installed.  This way I don't have to manually update GRUB everytime a new kernel update comes out, or delete every outdated kernel on my machine.  I've tried to figure this out on my own, but I'm not familiar with bash scripting and it's proven to be a bit overwhelming.  Can anyone provide some insight on how I might best accomplish this?

Thanks,

Mike

---

### Post by oldfred on 2009-12-13
I copied this from someone possibly ranch hand:

A menuentry like this should always use the latest entry:

menuentry "Latest Kernel" {
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 5a880a39-36a1-46f5-b106-e979608f295a
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
}
Just take your existing entry and remove the specific info from the end of the "vmlinuz" and "initrd" entries.

You could put it at the top of your menu by creating a 06_custom file. To hide the other entries, you could disable 10_linux if you really wanted to. But check that this entry works first, of course.

---

### Post by mclark1129 on 2009-12-14
oldfred,

Thanks for the response.  I opened grub.cfg and copied the entry generated for the latest kernel into the 40_custom file.  I removed the specific version number from the entry and updated grub.  When I tried to use the new entry in the menu I got the error: "e: You must first load the kernel" or something along those lines.  My 40_custom file is below:

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Ubuntu" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 2606999c-d421-44d7-a09a-e41820622f5f
    linux    /boot/vmlinuz root=UUID=2606999c-d421-44d7-a09a-e41820622f5f ro   quiet splash
    initrd    /boot/initrd.img
}

What is it that I'm doing wrong?

Thanks,

Mike

---

### Post by jocko on 2009-12-14
> **mclark1129 said:**
> 
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Ubuntu" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 2606999c-d421-44d7-a09a-e41820622f5f
    [COLOR=Red]linux    /boot/vmlinuz root=UUID=2606999c-d421-44d7-a09a-e41820622f5f ro   quiet splash
    initrd    /boot/initrd.img[/COLOR]
}

What is it that I'm doing wrong?
You need to point it to the symlinks /vmlinuz and /initrd.img (which always point to the latest kernel. There are no files named "/boot/vmlinuz" or"/boot/initrd/img"). So remove the "/boot" from the last two lines.

---

### Post by mclark1129 on 2009-12-14
That did the trick, thanks!

Mike

---

