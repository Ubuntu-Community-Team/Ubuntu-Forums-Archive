---
title: "GRUB 2 - Determine UUID for a hfsplus partition on GPT harddrive?"
date: 2012-05-24
forum: General Help
---

### Post by HarmCla on 2012-05-24
I have Mac OS X installed on my laptop, and whenever I do update-grub in ubuntu, it generates two entries for Mac OS X, like this one:

```

menuentry "Mac OS X (64-bit) (on /dev/sdb5)" --class osx --class darwin --class os {
    savedefault
    insmod part_gpt
    insmod hfsplus
    set root='(hd1,gpt5)'
    search --no-floppy --fs-uuid --set=root [COLOR=Red]95d9c170bdda9e94[/COLOR]
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume = 0 ]; then
           xnu_uuid [COLOR=Red]95d9c170bdda9e94[/COLOR] uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel64 /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}

```I don't understand where GRUB 2 gets that UUID from,
if I check GParted, the blkid command, or even in the Mac OS X terminal for the UUID, the UUID reads:[COLOR=Red] 05a5f7dc-f2ee-335d-bb81-ee874ea029ba[/COLOR].
Which doesn't even match close to GRUB's [COLOR=Red]95d9c170bdda9e94[/COLOR].

But I never worried about that, because to make GRUB 2 load
the Mac OS X bootloader, Chameleon, I modify the entry, like so:

```

menuentry "Mac OS X (64-bit) (on /dev/sdb5)" --class osx --class darwin --class os {
    savedefault
    insmod part_gpt
    insmod hfsplus
    set root='(hd1,gpt5)'
    search --no-floppy --fs-uuid --set=root [COLOR=Red]95d9c170bdda9e94[/COLOR]
    multiboot /boot
}

```And that always worked perfectly.

Now I copied the chameleon bootloader to the EFI partition,
but GRUB 2 doesn't seem to detect that, so I need to make my own entry.

I tried:

```

menuentry "Mac OS X (64-bit) (on /dev/sdb5)" --class osx --class darwin --class os {
     savedefault
     insmod part_gpt
     insmod hfsplus
     set root='(hd1,gpt[COLOR=Red]1[/COLOR])'
     search --no-floppy --fs-uuid --set=root [COLOR=Red]682265f3-9f3d-304c-b48e-e98051d12268[/COLOR]
     multiboot /boot
}

```But then GRUB 2 gives me an error saying 
No such device: 682265f3-9f3d-304c-b48e-e98051d12268
File not found

Clearly I need to find the shorter version of the UUID, but where can I find that? :(

Where does GRUB 2 get that shorter [COLOR=Red]95d9c170bdda9e94[COLOR=Black] UUID from anyway?

If any more info is required, I'll be happy to give you.
[/COLOR] [/COLOR]

---

### Post by ratcheer on 2012-05-24
Command "sudo blkid" should give you a list of the UUID's.

Tim

---

### Post by HarmCla on 2012-05-24
I swear I googled before I made a new thread,
but right after I posted the thread, I found the answer!

The command to find GRUB's version of the UUID is
**[COLOR=Red]sudo grub-probe -t fs_uuid /path/to/mounted/partition[/COLOR]**

So I gave that a try:
```
harm@Wildcat:~$ sudo grub-probe -t fs_uuid /media/MacOSX
95d9c170bdda9e94
harm@Wildcat:~$ 
```YES! The UUID matches the one in my grub.cfg!

So I mounted the EFI Partition, and re-ran the command:
```

harm@Wildcat:~$ sudo grub-probe -t fs_uuid /media/EFI
d14c83a4e47989e9
harm@Wildcat:~$

```And there's the UUID I needed! :p

Finally, my new entry to boot Chameleon of of the EFI partition,
(or really any other partition you want):

```
menuentry "Chameleon Bootloader (on EFI partition)" --class osx --class darwin --class os {
    savedefault
    insmod part_gpt
    insmod hfsplus
    set root='(hd1,gpt1)'
    search --no-floppy --fs-uuid --set=root [COLOR=Red]d14c83a4e47989e9[/COLOR]
    multiboot /boot
}
```Victory!

:guitar:

---

### Post by HarmCla on 2012-05-24
> **ratcheer said:**
> Command "sudo blkid" should give you a list of the UUID's.

Tim
Thanks for the fast reply Tim,
but, as I stated in my original post:

> if I check GParted, **the blkid command**, or even in the Mac OS X terminal for the UUID, the UUID reads:[COLOR=Red] 05a5f7dc-f2ee-335d-bb81-ee874ea029ba[/COLOR].
Which doesn't even match close to GRUB's [COLOR=Red]95d9c170bdda9e94[/COLOR].But nevermind, see my previous post, I found the solution.

Thanks!

---

### Post by ratcheer on 2012-05-24
Sorry, I didn't know there were different UUID's. Glad you found what you needed.

Tim

---

