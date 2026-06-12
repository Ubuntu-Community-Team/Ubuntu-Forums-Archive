---
title: "menu.lst issue"
date: 2009-12-07
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2009-12-07
i have a tripple boot
ubuntu 9.04 32bit
ubuntu 9.10 64bit
windows XP Pro

i prefer the old grub so i have it set to boot using the 9.04 partition
i just let it update i used the package maintainers version
but it will not boot with it
gives an error 17

```
title        kernel 2.6.28-17-generic
uuid         225560a9-194c-4aab-96df-af981c356f6f
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=225560a9-194c-4aab-96df-af981c356f6f ro quiet splash 
initrd        /boot/initrd.img-2.6.28-17-generic
quiet
```i fixed that with this

```
title        kernel 2.6.28-17-generic
root         (hd0,0)
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=225560a9-194c-4aab-96df-af981c356f6f ro quiet splash 
initrd        /boot/initrd.img-2.6.28-17-generic
quiet
```but it still does not boot
it is like it cant find something

edit form the new grub
```
menuentry "kernel 2.6.28-16-generic (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 08bad4f8-d123-4e3a-9381-2c21e3a25aeb
    linux /boot/vmlinuz-2.6.28-16-generic root=UUID=225560a9-194c-4aab-96df-af981c356f6f ro quiet splash
    initrd /boot/initrd.img-2.6.28-16-generic
}
```this was made before the last kernel update

EDIT:
fixed it for some reason it wanted to use the wrong uuid

---

