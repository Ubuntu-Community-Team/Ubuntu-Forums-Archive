---
title: "Killed my grub2 menu"
date: 2010-04-12
forum: General Help
---

### Post by gravyface on 2010-04-12
So, Googling around, trying to figure out how to use the "superior" GRUB2, and hosed my GRUB menu; only thing that's loading is the memtest.  Here's what I did:

chmod -x /etc/grub.d/10_linux  (<-- read that in order to remove menu items, you can remove the execute permissions from the script in question)

After copying what was in /boot/grub/grub.cfg to the 40_custom script, I edited the following:

```
### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

# aufs read-only grub menu items
menuentry "Ubuntu, Linux 2.6.31-20-generic **READ-ONLY**" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        set quiet=1
        insmod ext2
        set root=(hd0,1)
        search --no-floppy --fs-uuid --set 2f4daaaa-ec96-426c-be68-f4bb6bfe4166
        linux   /boot/vmlinuz-2.6.31-20-generic root=UUID=2f4daaaa-ec96-426c-be68-f4bb6bfe4166 ro   quiet splash **aufs=tmpfs**
        initrd  /boot/initrd.img-2.6.31-20-generic
}

menuentry "Ubuntu, Linux 2.6.31-20-generic **WRITEABLE**" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        set quiet=1
        insmod ext2
        set root=(hd0,1)
        search --no-floppy --fs-uuid --set 2f4daaaa-ec96-426c-be68-f4bb6bfe4166
        linux   /boot/vmlinuz-2.6.31-20-generic root=UUID=2f4daaaa-ec96-426c-be68-f4bb6bfe4166 ro   quiet splash
        initrd  /boot/initrd.img-2.6.31-20-generic
}

menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        insmod ext2
        set root=(hd0,1)
        search --no-floppy --fs-uuid --set 2f4daaaa-ec96-426c-be68-f4bb6bfe4166
        linux   /boot/vmlinuz-2.6.31-20-generic root=UUID=2f4daaaa-ec96-426c-be68-f4bb6bfe4166 ro single
        initrd  /boot/initrd.img-2.6.31-20-generic
}

### END /etc/grub.d/40_custom ###
```

Strings in bold are what I've added.

I then ran grub-update and rebooted and all I get is (what I assume to be) Memtest or whatever entry that I left in there and itself is giving an error:

```
error: too small lower memory (0x99100 > 0x8f000)

Failed to boot default entries
```


I'm assuming 40_custom was executable because I could see the "how to" text from that script being written to grub.cfg before I reloaded it.

---

### Post by prodigy_ on 2010-04-12
Boot from Ubuntu Live CD. Chroot into your Linux installation. Assuming that UUIDs in your 40_custom are correct: ```
sudo mount -U 2f4daaaa-ec96-426c-be68-f4bb6bfe4166 /mnt
sudo mount --bind /dev /mnt/dev
sudo chroot /mnt
``` Then you'll be able to undo whatever changes you made earlier.

---

### Post by gravyface on 2010-04-12
I just mounted the drive (it's a CF card on a CF2Sata enclosure) in my other working server and am reversing my execute/40_custom changes.

Any idea what's wrong?

---

### Post by prodigy_ on 2010-04-12
Well, first of all, don't disable **10_linux** until you're sure that **40_custom** works as you want. And when it does, if you want to see only the entries from your **40_custom**, disable **20_memtest86+** and **30_os-prober** as well.

---

### Post by darolu on 2010-04-12
Configuring the custom file alone doesn't work; remember you have to run:
```
$ sudo update-grub
```

Try deleting all entries from 40_custom and then run update-grub (all in chroot session like prodigy told you).

Anyways, if you just want to change the menuentry string, editing the /boot/grub/grub.cfg file directly works (don't run update-grub after editing or it will restore the values):
```
$ gksu gedit /boot/grub/grub.cfg
```
Edit the menuentry strings **only**.

---

### Post by gravyface on 2010-04-12
Hmm, i removed all my changes from grub.cfg (doing the CF mount from another server as I don't have a CD drive; will make a USB livecd again if I have to) so it now looks identical (or so I think) to what it had before, and still getting "failed to boot default entries".

---

### Post by gravyface on 2010-04-12
Ok, I moved up my 40_custom lines (the original 10_linux generated lines) to right after the 0_header lines and it boots now.

I've since edited the grub.cfg again and added my aufs=tmpfs arguments and that's working as expected too.

My question now is: how am I supposed to replace the "default" 10_linux generated menu items with my own custom menu items?  Should I create my own 10_gravyface_linux script and chmod -x the 10_linux one?

Clearly my 40_custom experiment didn't work.

---

### Post by oldfred on 2010-04-13
Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)

I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
In /etc/default/grub I added this:
GRUB_DISABLE_OS_PROBER=true

---

### Post by gravyface on 2010-04-13
Thanks for that oldfred, but wow, GRUB2: over-engineer much?

---

