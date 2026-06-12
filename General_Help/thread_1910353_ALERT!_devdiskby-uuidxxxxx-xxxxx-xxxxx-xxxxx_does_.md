---
title: "ALERT! /dev/disk/by-uuid/xxxxx-xxxxx-xxxxx-xxxxx does not exist"
date: 2012-01-17
forum: General Help
---

### Post by russ_kz on 2012-01-17
Gents,

Could you please advise what might be causing this error while booting through menu entry ('Ubuntu, with Linux 2.6.38-11-generic'):

ALERT! /dev/disk/by-uuid/xxxxx-xxxxx-xxxxx-xxxxx does not exist
Dropping to a shell

Although I can boot Ubuntu without any problem through this menuentry:
'Ubuntu, with Linux 2.6.35-31-generic'

Thank you for your support

Russ

---

### Post by Xgen on 2012-01-17
Obviously that UUID doesn't relate to anything. You could try refreshing/updating your grub menu.

'sudo update-grub2'

---

### Post by russ_kz on 2012-01-17
> **Xgen said:**
> Obviously that UUID doesn't relate to anything. You could try refreshing/updating your grub menu.

'sudo update-grub2'


Unfortunately this update didn't help much.

Please see below extract from grun.cfg

Seems 'Ubuntu, with Linux 2.6.38-11-generic' refers to the same UUID as ''Ubuntu, with Linux 2.6.35-31-generic' does. However I am able to boot through ''Ubuntu, with Linux 2.6.35-31-generic'  

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 0f3b0a49-25c4-4864-9349-4592a000fad5
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=0f3b0a49-25c4-4864-9349-4592a000fad5 ro   
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 0f3b0a49-25c4-4864-9349-4592a000fad5
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=0f3b0a49-25c4-4864-9349-4592a000fad5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 0f3b0a49-25c4-4864-9349-4592a000fad5
    linux    /boot/vmlinuz-2.6.35-31-generic root=UUID=0f3b0a49-25c4-4864-9349-4592a000fad5 ro   
    initrd    /boot/initrd.img-2.6.35-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 0f3b0a49-25c4-4864-9349-4592a000fad5
    echo    'Loading Linux 2.6.35-31-generic ...'
    linux    /boot/vmlinuz-2.6.35-31-generic root=UUID=0f3b0a49-25c4-4864-9349-4592a000fad5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-31-generic
}

---

### Post by gsgleason on 2012-01-17
Please show the output of 'sudo blkid'

---

