---
title: "Adding a mandriva installation to grub ?"
date: 2010-05-07
forum: General Help
---

### Post by Mysticaly on 2010-05-07
I'm trying to add mandriva to grub2 and have difficulties..

Mandriva has it own boot partition on sda1 (ext3) Ubuntu boots in /boot on ubuntu's / partition which is sdb6
Mandriva / partition is: sda5 (ext4) 
UUID for Mandriva boot partition is: bf53ebd1-4698-4522-ae0d-f9465aa2f0a3 (sda1)
UUID for Mandriva / is: 658bcd3e-9c69-49c9-8da1-a7e0b9723547 (sda5)
UUID for Mandriva swap is: d3bc2559-4f86-4269-bf25-c99e726c8775 (sda7)

Ive made a file which I have put in /etc/grub.d/ so each time I run update-grub2 it also includes this script.

```
echo "Adding Mandriva 2010.1" >&2
cat << EOF
menuentry "Mandrivas 2010.1, linux 2.6.33.3" {
        insmod ext2
        set root='(hd0,0)'
        search --no-floppy --fs-uuid --set bf53ebd1-4698-4522-ae0d-f9465aa2f0a3
        linux /vmlinuz BOOT_IMAGE=linux root=UUID=bf53ebd1-4698-4522-ae0d-f9465aa2f0a3 resume=UUID=d3bc2559-4f86-4269-bf25-c99e726c8775 splash=silent vga=788
        initrd (hd0,1)/initrd-2.6.33.3-desktop586-1mnb.img
}

EOF
```

It gives error kernel panic, and something with initrd beeing shut down before completion

---

### Post by mechro on 2010-05-07
Have you run **sudo update-grub**? This should find other operating systems and put them in grub.cfg.

---

### Post by Mysticaly on 2010-05-07
of-course I have, unless I had I could never have added anything to the grub menu in the first place could I, and no, I'm afraid that doesn't help me much as it adds with totally wrong locations..

---

### Post by oldfred on 2010-05-07
The separate /boot is confusing both me & grub2. I do not use a separate /boot but have seen a few.

Your set root is to a partition that does not exist in grub2. It changed number so the first partition is (hd0,1).

Where are the kernel images, are they not in /boot in the boot partition. If so your entry should also have that.

Your set root says to use the boot partition, should that not be the root partition's UUID?

I would make those changes and if it does not work use manual editing from the grub menu to test alternatives.

---

### Post by mechro on 2010-05-07
> **Mysticaly said:**
> of-course I have, unless I had I could never have added anything to the grub menu in the first place could I

Gee, you're assuming I'm quite intelligent. ;)

Does Mandriva use Grub Legacy? There's probably a conflict.

Does this help?...

[http://forums.scotsnewsletter.com/index.php?showtopic=30224](http://forums.scotsnewsletter.com/index.php?showtopic=30224)

---

### Post by x-shaney-x on 2010-05-07
```
menuentry "Mandrivas 2010.1, linux 2.6.33.3" {
        insmod ext2
        set root='[COLOR=Red](hd0,0)[/COLOR]'
        search --no-floppy --fs-uuid --set bf53ebd1-4698-4522-ae0d-f9465aa2f0a3
        linux /vmlinuz BOOT_IMAGE=linux root=UUID=bf53ebd1-4698-4522-ae0d-f9465aa2f0a3 resume=UUID=d3bc2559-4f86-4269-bf25-c99e726c8775 splash=silent vga=788
        initrd [COLOR=Red](hd0,1)[/COLOR]/initrd-2.6.33.3-desktop586-1mnb.img
```

[COLOR=Red]HERE[/COLOR] is your problem.
I had the same problem with Mandriva and PCLinuxOS, which both use grub legacy.
Not only does ubuntu's grub see the initrd on a different partition but that second partition entry doesn't need to be there at all.
In the short term you could edit the entry from the grub menu to remove the (hd(0,1) on the initrd line to get it to boot.
In the long term you will probably need to create a custom entry in /etc/grub.d/40_custom.
That is how I dealt with it.

---

