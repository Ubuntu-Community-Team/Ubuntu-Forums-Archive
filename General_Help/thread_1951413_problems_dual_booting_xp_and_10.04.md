---
title: "problems dual booting xp and 10.04"
date: 2012-04-02
forum: General Help
---

### Post by mejbr2003 on 2012-04-02
twice now I've tried installing lucid along side xp using the usb installer.
it installs fine, but when I restart, xp won't boot.
it says" card read error, cntrl+al+del to reboot"
it never boots.
so twice, I've wiped the drive and reinstalled xp then lucid
with the same problem.
I generally use ubuntu, but like to have xp for a few things...
why is this happening?
thanks for any help

---

### Post by imachavel on 2012-04-02
wait you are installing by creating new partitions by booting to a disk partitioner like gparted? Or through windows wubi with the disk after windows file system, boots, mounts, and loads?

Oh lord

download boot repair disk from this site:

[http://sourceforge.net/projects/boot-repair-cd/](http://sourceforge.net/projects/boot-repair-cd/)

then burn the .iso to a cd, then put the cd in the drive, and run the cd, then click 'create boot info script' button, and once the boot info script text file has been saved, upload it to this thread as an attachment, and I guess we'll take a look at your grub

---

### Post by mejbr2003 on 2012-04-02
to be clear, at this time, after wiping my hd, I have only installed xp.

the two previous tries, I installed xp used the usb installer, rebooted and then followed ubuntu set up procedure giving xp 70gb
and lucid 130gbs.

I don't know anything about gparted...and the download page didn't say anything about it

how should I go about installing lucid properly?

---

### Post by imachavel on 2012-04-02
so xp is installed on a 70 gb partition? and lucid not installed? first thing is first, download gparted:

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

burn it to a disk and boot to it. Now this will make it simple:

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

verify you have two partitions. If not create a new partition in the empty space, assign ext2 file system, and then click 'apply'
Now that you are there. verify a swap space has been created. So you should ntfs on a 70gb space, and ext2 on a 130gb space. If so, good!

Now that you are finished there, reboot with your Ubuntu disk in the cd tray, and from bios select to boot from cd drive(you know how to do all of that?):

[http://www.simplyguides.net/guides/boot_from_cd/boot_from_cd.shtml](http://www.simplyguides.net/guides/boot_from_cd/boot_from_cd.shtml)

(it's not always delete, sometimes it's f2 or f12.) And sorry if I forgot to mention you need to set that boot order to boot to g parted as well. Now when Ubuntu loads up, you can choose to use it as a live cd, or you can choose to install it. When you choose to install it, it will ask you which partition to install Ubuntu on. Choose the one you created in g parted. Now that you have accomplished this, it should be installed!

How does it load up? drivers all good? Once it loads go back into this thread, and after opening a terminal:

ctrl+alt+t

please type in:

lspci, and post return syntax. You will need all codecs and plug ins to watch youtube and hear sound, also brand new linux installs seem to have gnome sound muted for some reason. Should be that simple. I don't recommend wubi, windows FAILS, often. It's a great simply interface the world loves. But be sure to understand, don't install linux through wubi. Usb installer? Did you boot to the usb? Or put ubuntu 11.4 or 11.10 .iso on the usb and install that way once windows loaded up? Did I help you at all? Let me know

---

### Post by mejbr2003 on 2012-04-02
sorry, no...
currently i have xp alone on a 200gb hd....should I proceed as you suggest?

---

### Post by imachavel on 2012-04-02
I don't see why not. what could it hurt. Before you proceed please upload a boot info script, to do so download:

[http://sourceforge.net/projects/boot-repair-cd/](http://sourceforge.net/projects/boot-repair-cd/)

burn the .iso to disk. Then run the disk and upload a boot info script from windows. I would try as suggested with gparted, but if you want a fail safe view everyone can see, the boot info script uploaded as an attachment, surely would tell every forum user what is going on with your bios and hdd, so any member that sees this thread can confirm, to go ahead and use gparted. Gparted is the safest bet if used correctly. Good luck and let us know your progress

---

