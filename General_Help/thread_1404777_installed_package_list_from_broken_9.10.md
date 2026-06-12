---
title: "installed package list from broken 9.10"
date: 2010-02-11
forum: General Help
---

### Post by itchaka on 2010-02-11
How can I get a list of all installed packages from a 9.10 that doesn't boot but that I have access to all files ?

---

### Post by Satoru-san on 2010-02-11
no, dont fix it that way.

I need more details to tell you how to fix your computer, but you can still boot into the broken ubuntu by following these steps. Once you do you are able to fix whatever is keeping it from booting.

boot the live cd and choose try without changes to harddrive.
Open up a terminal
```
sudo mkdir /mnt/ubuntu
sudo mount /dev/sda1 /mnt/ubuntu
sudo chroot /mnt/ubuntu
```Replace sda1 with the / partition of your ubuntu.

This gives you root access to your computer, you can run apt and any other command that requires root without sudo.

Good luck, let us know some more details.


P.s. if you could please post in ```
 tags your dmesg

[code]dmesg > ~/dmesg
gedit ~/dmesg
```

---

### Post by samantha_ on 2010-02-11
boot using a livecd.
run this (replace sdax with your partition)
```

sudo mount -t ext4 /dev/sdax /mnt
sudo chroot /mnt

```
then
```
 dpkg --get-selections > ~/installed-software
exit

```
```

sudo mv /mnt/root/installed-software ~/Desktop/installed-software

```
copy that file on your desktop to a usb drive or upload it somehwere.
on the new installation, put the file on the desktop.
run
```
sudo dpkg --set-selections < ~/Desktop/installed-software
dselect
```

Its a modified version of the instructions from [http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)

---

### Post by itchaka on 2010-02-11
Thanks for quickness, solution worked perfectly !

@samantha thanks also ! it was the chroot part i couldnt figure out...

---

