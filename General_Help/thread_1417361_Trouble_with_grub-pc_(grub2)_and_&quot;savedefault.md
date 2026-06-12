---
title: "Trouble with grub-pc (grub2) and &quot;savedefault&quot;"
date: 2010-02-27
forum: General Help
---

### Post by pseudomino on 2010-02-27
Hello everybody

Since karmic I'v got an issue with the fonction "savedefault" (remember the last entry booted).

I put 
**GRUB_DEFAULT=saved**
(I also tried with "saved" according to other sources)

but it has no effect.

Is there any other setting I have to change?

Thanxx!

---

### Post by dino99 on 2010-02-27
fresh install or dist-upgrade ?
if you have both grub-pc and grub-legacy, you might remove/purge everything about grub (1 & 2) with synaptic (complete remove) then reinstall only: 
- grub-pc
- grub-common
- startupmanager

into console then run:
- grub-mkconfig
- update-grub

then reboot and run startupmanager if needed.

note: when building grub.conf, the settings are picked from /etc/default/grub

here is mine:
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

---

### Post by pseudomino on 2010-02-27
> fresh install

my  /etc/default/grub is the same, with

GRUB_DEFAULT=saved

instead of 0

so... uh ?

---

### Post by pseudomino on 2010-03-02
up!
please could you just confirm me that your grub is able to record the last booted entry?

and if you're very kind, what you did to obtain that?

---

### Post by pseudomino on 2010-03-08
Ok... the problem was just that I didn't add manually 
"    saved_entry=${chosen}
    save_env saved_entry "

to the 40_custom file (in /etc/grub.d )

Fixed!

---

### Post by patchwork on 2010-03-08
...or you could try
```
sudo grub-set-default N
``` Where N is the menu entry (counts from 0)

---

### Post by kstevens on 2010-05-11
Ran into this same issue on a recent upgrade to Lucid Lynx.

You need to add both of these lines:
```
GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true
```to /etc/default/grub, then run "sudo update-grub"

Check the entries in /boot/grub/grub.cfg and they should look something like:
```
### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        savedefault
        insmod ext2
        set root='(hd0,5)'
        search --no-floppy --fs-uuid --set c23bb931-2d60-4f48-9086-c8dbdc7fdca6
        linux   /boot/vmlinuz-2.6.32-22-generic root=UUID=c23bb931-2d60-4f48-9086-c8dbdc7fdca6 ro splash vga=786  quiet splash
        initrd  /boot/initrd.img-2.6.32-22-generic
}
```Note the line that says "savedefault".  That indicates that this menu entry will save itself as the default when selected.  You should see it on each menu entry.

---

### Post by osarusan on 2010-05-17
Thanks guys! I searched for about an hour and couldn't find anything until I came upon this thread. I do believe you're the only two to have given a clear-cut answer to this problem so far!

---

