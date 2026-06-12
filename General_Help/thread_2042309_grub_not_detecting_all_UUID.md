---
title: "grub not detecting all UUID"
date: 2012-08-14
forum: General Help
---

### Post by rocketscove on 2012-08-14
I am using ubuntu 12.04 in dual boot with w7, mepis11, mepis85 plus... Update-grub does not  include UUID for one of the boot stanza's. I tried to edit /etc/grub.d/ 40_custom to correct this but got errors on running update-grub. The following is from /boot/grub/grub.cfg and the problem is in the line:

 ```
 linux /boot/vmlinuz root=/dev/sda11 nomce quiet splash vga=788
```I would like to have that line read : ... root=UUID=ac5e4136-7bc5-4a0f-8d45-e201caf3176c...  similar to the mepis85 entry. 

```

### BEGIN /etc/grub.d/30_os-prober_proxy ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    savedefault
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 15D5E140501B7227
    chainloader +1
}
menuentry "MEPIS at sda11, newest kernel (on /dev/sda11)" --class gnu-linux --class gnu --class os {
    savedefault
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set=root ac5e4136-7bc5-4a0f-8d45-e201caf3176c
    linux /boot/vmlinuz root=/dev/sda11 nomce quiet splash vga=788
    initrd /boot/initrd.img
}
menuentry "MEPIS new 8.5 at sda5, newest kernel (tv sorta) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    savedefault
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 0de66daf-a328-43c2-b264-dd4c24739978
    linux /boot/vmlinuz root=UUID=0de66daf-a328-43c2-b264-dd4c24739978 nomce quiet splash vga=789 nomodeset nouveau.modeset=0
    initrd /boot/initrd.img
```What am I doing wrong or what can I do to correct this??? 

The machine is booting correctly, but I know I will gparted something to change the /dev/sdax designation.

---

### Post by oldfred on 2012-08-14
I keep installing Ubuntu and have so many old one's I do not want the os-prober to find them. I turn off the os-prober after backing up a copy of grub.cfg. And then copy only those boot stanza's I want into 40_custom.

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

OR Partial Custom menu:
I  turned off os-prober so it does not look for other systems and totally customized my 40_custom.
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

Copy the  entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit:
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

---

### Post by rocketscove on 2012-08-14
Thanks for prompt reply.
> Copy the  entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit:
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub 	

That is exactly what I tried first...but....got syntax errors. Probably my typing or pasting...

The problem that really bugs me is: Why does the os_prober get the uuid correct (two places) for the mepis85 stanza, BUT does not include the uuid in the mepis11 stanza?????

---

### Post by oldfred on 2012-08-14
I thought the os-prober copied the boot stanza from a grub.cfg, menu.lst or grub.conf if found, but it must also try to build a boot stanza. Not sure why otherwise.

Some with Fedora have to add the lvm2 driver & mount the partition to get the os-prober to even see the Fedora to add a boot stanza.

---

