---
title: "error: unknown file system. grub rescue &gt; error! help please!"
date: 2011-08-29
forum: General Help
---

### Post by NattyNoobCake on 2011-08-29
i was dual booting win7 and ubuntu 11.04. i deleted the ubuntu partition because i wanted to completely wipe and reinstall ubuntu...but when i try to restart, it only says

```

error: unknown filesystem
grub rescue>

```

i don't know what this means..(i'm sorry i'm new to linux). i tried getting the liveCD for ubuntu on a USB and booting from that but i get the same error :(
what do i do??
i don't care if i lost all my ubuntu partition data. I have it all backed up

---

### Post by NattyNoobCake on 2011-08-29
please PLEASE help :(

---

### Post by raja.genupula on 2011-08-29
its seems you're not booting from either cd or usb . check primary boot in your bios . set it to cd or usb to boot from them .

---

### Post by NattyNoobCake on 2011-08-29
ok now i really don't know what to do
i put ubuntu's install on a usb and booted to that. the install went fine and told me to restart. upon restarting, i got the same grub error. 

so i tried installing again. This time, when i try to boot, it doesn't even show the grub error. it just has a blinking underslash "_" in the top left corner


if anyone can help PLEASE PLEASE help me.........im completely new to ubuntu and at the moment, my computer is completely useless :(

---

### Post by westie457 on 2011-08-29
> **NattyNoobCake said:**
> ok now i really don't know what to do
i put ubuntu's install on a usb and booted to that. the install went fine and told me to restart. upon restarting, i got the same grub error. 

so i tried installing again. This time, when i try to boot, it doesn't even show the grub error. it just has a blinking underslash "_" in the top left corner


if anyone can help PLEASE PLEASE help me.........im completely new to ubuntu and at the moment, my computer is completely useless :(

Hi.
Go through the install process again and at the where to install scree choose 'Something Else'. In the partitioning screen choose the same partition as EXT4, In the small box under this put a check mark to format and then in the next box 'Use As' take the first option to use as / (root).

If you have/had a separate /Home partition repeat the above for that.

At the bottom of this screen is the option for where to install Grub choose to install Grub to the MBR of the hard drive /sda. The hard drive will be identified with the manufacturers name.

All this should clear the errors you have at the moment.

---

### Post by NattyNoobCake on 2011-08-29
> **westie457 said:**
> Hi.
Go through the install process again and at the where to install scree choose 'Something Else'. In the partitioning screen choose the same partition as EXT4, In the small box under this put a check mark to format and then in the next box 'Use As' take the first option to use as / (root).

If you have/had a separate /Home partition repeat the above for that.

At the bottom of this screen is the option for where to install Grub choose to install Grub to the MBR of the hard drive /sda. The hard drive will be identified with the manufacturers name.

All this should clear the errors you have at the moment.

i can't go through the install again. When i boot from USB, all that happens is i see a blinking "_" sign in the top left corner

---

### Post by westie457 on 2011-08-29
Which program did you use to create the LiveUSB ?

---

### Post by NattyNoobCake on 2011-08-29
i've actually tried multiple :(
1)UltraISO
2)The one recommended by on the Ubuntu site
[http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer.exe]("http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer.exe")
3)LinuxLive creator 2.8.4

---

### Post by NattyNoobCake on 2011-08-29
okay, so i just tried burning it onto a disk b/c i thought the problem was with the usb drive. This worked fine and i got the ubuntu loader 
but now i have another problem it says
```

BusyBox v1.17.1 (Ubuntu 1:1.17.1-10ubuntu1) built in shell (ash)
(initramfs) mount : mounting /dev/loop0 on //filesystem.squashfs failed:input/output error. Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

```

i have **_no_** idea what this means or how to fix it
any help would really be appreciated as i have a lot of work to do on my broken computer :(

---

### Post by raja.genupula on 2011-08-30
> **NattyNoobCake said:**
> i've actually tried multiple :(
1)UltraISO
2)The one recommended by on the Ubuntu site
[http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer.exe]("http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer.exe")
3)LinuxLive creator 2.8.4

ubuntu have one start up disk creator , that's works fine for me many times, recently i am done with xubuntu installation also .
try that once .

---

