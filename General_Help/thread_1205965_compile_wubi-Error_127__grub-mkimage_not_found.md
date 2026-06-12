---
title: "compile wubi-Error 127 // grub-mkimage :not found"
date: 2009-07-06
forum: General Help
---

### Post by paok4 on 2009-07-06
I am compiling wubi for use with a custom ubuntu iso and i always get this error and no wubi.exe of course !!!!


```
make[1]: Leaving directory `/home/user/wubi/wubi/build/grubutil/grubinst'
mkdir -p build/winboot
cp -f data/wubildr.cfg build/winboot/wubildr.cfg
./build/grubutil/grubinst/grubinst --grub2 --boot-file=wubildr -o build/winboot/wubildr.mbr
grub-mkimage -c build/winboot/wubildr.cfg -o build/grubutil/core.img \
        pc fat ntfs biosdisk multiboot normal boot serial test hello terminfo \
        gpt ntfscomp search linux boot cat cpuid echo fshelp fs_uuid ls \
        chain halt help ls reboot sleep vbe pc loopback iso9660 ext2 configfile
sh: grub-mkimage: not found
make: *** [winboot2] Error 127
```what i do is 

mkdir wubi
cd wubi
bzr branch lp:wubi
cd wubi 

then i do the changes in the isolist.ini file like this 

>  [myiso]
version=1.0
info_file=.disk/info
kernel=casper/vmlinuz
initrd=casper/initrd.gz
files_to_check=casper/filesystem.squashfs
md5sums=md5sum.txt
metalink_md5sums=MD5SUMS-metalink
metalink_md5sums_signature=MD5SUMS-metalink.gpg
size=0
min_iso_size=600000000
max_iso_size=900000000
min_disk_space_mb=3000
min_memory_mb=256
support=http://www.ubuntu.com/support
installation_dir=ubuntu
#NOTE: installation_dir must also be changed in data/wubildr.cfgi place of course my custom images into the images directory

then i do "make" and the script goes all right (i accept the installations of wine e.t.c.) but at the end i always get the same error !!!

what exactly is wrong here ??? 

and a few more questions ... How i can disable the need for metalink file check/ md5 checksums / and need for singning key in this wubi version ??? the custom.iso  i want to use is only on my pc !!!

Any help please ???

---

