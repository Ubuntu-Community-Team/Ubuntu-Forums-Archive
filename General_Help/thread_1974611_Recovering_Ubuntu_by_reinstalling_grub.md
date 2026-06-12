---
title: "Recovering Ubuntu by reinstalling grub"
date: 2012-05-06
forum: General Help
---

### Post by itagomo on 2012-05-06
Before I had 3 partitions in my harddrive:
windows 7
ubuntu 11.04 natty
personal files drive

then I downgraded win 7 to win xp but windows installed it's own bootloader. Now I can't access Ubuntu drive. Fortunately, I have Ubuntu LiveUSB, boot into it and followed the steps in [https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)

tried Boot-Repair but getting an eror that it can't load some stuffs.

copied liveCD (or liveUSB) files with grub-install command. same issue.

copied partition files with grub-setup command. afterwards, i got a blank screen without any boot loader. getting a blank screen at boot worried me too much. i went back to liveUSB and performed the ChRoot option

note: /dev/sda5 is the Ubuntu partition.

sudo mount /dev/sda5 /mnt/
for i in /dev/ /dev/pts/ /proc/ /sys/; do sudo mount -B $i /mnt$i; done
sudo chroot /mnt/
update-grub
grub-install /dev/sda
grub-install --recheck /dev/sda

didn't get any error message

it successfully restored my Windows Bootloader but not Grub so back to zero. will purging and reinstalling grub be my last option? by the way, my installed distro version is 11.04 Natty but my LiveUSB is 10.04 Lucid. Is it a problem?

---

### Post by oldfred on 2012-05-06
From Boot-Repair post the link after running the Boot-INfo report. Then we can see you entire configuration and suggest possible solutions.

---

### Post by itagomo on 2012-05-07
i'll get back to you as soon as I install boot repair. do i need to use ChRoot to install it or just use it within the liveUSB session?

---

### Post by itagomo on 2012-05-07
successfully installed boot repair to my Ubuntu 11.04 using ChRoot that is with the ubuntu 10.04 liveUSB (i hope i don't confuse you)

don't know how to run it so I just entered the command within ChRoot:
[B]root@ubuntu /: boot-repair
[/B]
but displayed this error:
ERROR:root:Could not find any typelib for AppIndicator3

(glade2script:4052): Gtk-WARNING **: Could not load image 'os-uninstaller.png': Failed to open file '/usr/share/boot-sav/os-uninstaller.png': No such file or directory

(glade2script:4052): Gtk-WARNING **: Could not load image 'os-uninstaller.png': Failed to open file '/usr/share/boot-sav/os-uninstaller.png': No such file or directory
Traceback (most recent call last):
  File "/usr/bin/glade2script", line 4827, in <module>
    m = Gui()
  File "/usr/bin/glade2script", line 1932, in __init__
    self.parse_xml()
  File "/usr/bin/glade2script", line 1326, in parse_xml
    except gi._glib.GError, e:
AttributeError: 'module' object has no attribute '_glib'

exit ChRoot and installed boot repair in the liveUSB

another error, python is not compatible, here it is:

[B]dpkg: dependency problems prevent configuration of boot-repair-ubuntu:
 boot-repair-ubuntu depends on python (>= 2.7); however:
  Version of python on system is 2.6.5-0ubuntu1.
dpkg: error processing boot-repair-ubuntu (--install):
 dependency problems - leaving unconfigured[/B]

i'm doing the hard way to install them (liveUSB doesn't recognize my usb broadband so what i did is to download the deb files from another computer, go back to liveUSB and issue dpkg command from the terminal)

any suggestions that will make it easier?

---

### Post by oldfred on 2012-05-07
Boot-Repair does not require a chroot to run. You just run it from your liveCD or USB or download its full liveCD to run.

I think your chroot install of it was not finding all the parts of Boot-Repair as that is not how it is intended to work. Just run it.

---

### Post by itagomo on 2012-05-07
liveUSB will not run boot repair as the python within it is not updated to what the program needs.

i'll now try to purge grub and re-install a new one, i hope it's not a bad idea ..

---

### Post by itagomo on 2012-05-13
did install 12.04 instead ..

---

