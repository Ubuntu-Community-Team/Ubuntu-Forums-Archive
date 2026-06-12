---
title: "No Bootloader after kernel update, update-grub hangs."
date: 2010-12-01
forum: General Help
---

### Post by dexterchief on 2010-12-01
Well the title says it all. Ran the updater, went to boot to Win7 to use Photoshop and realized that the grub menu was gone. Ubuntu boots by default now. I tried running "sudo update-grub" at a virtual terminal and while it listed the various linux kernels ok, it then got caught in a loop spitting out some crazy looking errors.

I rebooted and Ubuntu came up fine. I tried running "sudo update-grub" again from the gnome terminal and it hangs the whole computer for a few minutes and finally gives me this:

> mike@sleepycat:~$ sudo update-grub
[sudo] password for mike: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found memtest86+ image: /boot/memtest86+.bin
done
mike@sleepycat:~$ 



> mike@sleepycat:~$ uname -a
Linux sleepycat 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 11:55:36 UTC 2010 x86_64 GNU/Linux

Any thoughts or guidance would be appreciated.

---

### Post by oldfred on 2010-12-01
Post this so we can see what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] here [ /code] tags.

You should keep one older kernel just in case but can delete others, just be sure not to delete the one you are using:
Go to Synaptic Package Manager and search for linux-image.

---

