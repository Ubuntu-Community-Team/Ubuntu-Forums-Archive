---
title: "Restore software packages from a broken Ubuntu installation using a live cd"
date: 2009-12-29
forum: General Help
---

### Post by RodGer GR on 2009-12-29
I installed Karmic on a friend's laptop and also installed all the needed programs. Something went wrong and I can't boot this installation anymore and I'll try to reinstall.

Is there a way to get the installed packages from the old installation using a live cd?
Or, at least, is there a way to get a list of the Synaptic markings so that I can do 'read markings' when I reinstall ?

Thanks for reading.
Thanks twice if you have any ideas!

---

### Post by iponeverything on 2009-12-29
I would use the liveCD to boot to the partition to see I could fix the existing install first.

---

### Post by RodGer GR on 2009-12-29
There are many problems with the existing installation.  I would probably have to reinstall the kernel AND Grub2. I tried to do that too booting a live cd and chroot-ing to the old installation but I didn't make it.

If anyone could give me detailed directions to reinstall the kernel and grub, maybe I would give it one more try.

Thanks a lot :guitar:

---

### Post by sisco311 on 2009-12-29
assuming that /dev/sda1 is the root partition:
```
sudo mkdir /mnt/ubuntu
sudo mount /dev/sda1 /mnt/ubuntu
sudo mount --bind /dev/ /mnt/ubuntu/dev
sudo mount --bind /dev/pts /mnt/ubuntu/dev/pts
sudo mount -t proc none /mnt/ubuntu/proc
sudo mount -t sysfs none /mnt/ubuntu/sys
sudo mount -o bind /etc/resolv.conf /mnt/ubuntu/etc/resolv.conf

```

EDIT3:
```
xhost +
```

```
sudo chroot /mnt/ubuntu
```

run:
```
synaptic
```
go to File -> Save Marking As..., select the *Save full state, not only changes* check box and save the markings in the root ("/") of the filesystem.

EDIT1: you can try to reinstall the kernel via synaptic.

EDIT2: to reinstall grub:
```
update-grub
grub-install /dev/sda
sudo grub-install --recheck /dev/sda
```
replace sda with the actual device name.

for more details see: [https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD")

exit from the chroot:
```
exit
```

backup the file: 
```
sudo cp /mnt/ubuntu/**filename** /media/**partition**
```

---

### Post by RodGer GR on 2009-12-29
That's one of the most helpful answers I've ever got. Not only I saved the synaptic markings this way but I really managed to make the old installation bootable again.

I didn't know which directories I should mount where so that I could make synaptic graphically accessible from chroot....

[U]If anyone has any relative documentation or manuals, I would be grateful. I'm willing to really learn how linux works so that I can help others too.
[/U]
Thanks a lot sisco311. You're great!

---

### Post by larrybalz on 2010-12-20
Very Impressive work you have there but it did not work for me..
I am stuck at the Synaptic stage.
I run 
[code] synaptic
go to File -> Save Marking As..., select the Save full state, not only changes check box and save the markings in the root ("/") of the filesystem.

When i save i get an error message "Can't Write /"

Please any help would be appreciated

---

