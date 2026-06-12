---
title: "Linux disappeared when i reinstalled windows"
date: 2006-04-23
forum: General Help
---

### Post by Minn3h on 2006-04-23
I had Linux booting perfectly with GRUB, but my windows install died so I had to reinstall.  And of course windows likes to do whatever it wants.  How do I get back to my GRUB menu?

---

### Post by echo $USER on 2006-04-23
If you have a Live CD(Ubuntu Live CD would be a good choice) then you can bring back your Ubuntu grub menu. Just boot with the live CD. It should detect all your partitions and say your Ubuntu partition is on hda5 and IS mounted, if live CD has detected everything then your partition should be at
Code:

/media/hda5


now do this

Code:

chroot /media/hda5


this will put you into you installed system any change you make will be applyed to you installed system

now reinstall grub using

Code:

grub-install /dev/hda


you'll have your grub boot loader back

---

### Post by issueperson on 2006-04-23
[QUOTE=Minn3h]I had Linux booting perfectly with GRUB, but my windows install died so I had to reinstall.  And of course windows likes to do whatever it wants.  How do I get back to my GRUB menu?[/QUOTE]

did you have GRUB installed on your linux partition or the master boot record?

if you had it installed your linux partition, you'll just have to change that partition to the bootable partition from windows (don't do that unless you know what you're doing).
if you had it on the MBR, windows might have erased it.
in that case, you can use the ubuntu install CD:

[http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+crashed]("http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+crashed")

issueperson

---

### Post by Minn3h on 2006-04-23
I don't know where it was but Echo's directions worked perfectly.

---

### Post by catlett on 2006-04-23
Just to clarify. Linux didn't go anywhere. Windows erased Grub and installed it's own bootloader. The windows bootloader will not recognise a non-windows system and will not give you an option to boot to it. Also it will erase the bootloader you have installed without so much as a prompt saying it is about to do it. Nevermind a prompt giving you the option to not install the windows boot loader. (see why we all hate the imperialistic nature of Microsoft)
What echoes directions did was re-install Grub via the command line of the live cd.
The linux bootloader(the good guys) recognises and gives you the option to boot to another os. If for some reason you have to re-install Windows and Linux, always do windows first and Linux second because the linux loader will give you a linux and windows option at boot but windows will only give you a windows option.
Bookmark this post because sometimes Grub will come up with an error 17 or 22 and you will need these directions to re-install Grub.
Well glad you're up and running, there are alot of Grub error problems out there so pass along this info on the forums when you see someone struggling with grub. Regards.

---

