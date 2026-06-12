---
title: "GRUB2 has no entries"
date: 2010-07-11
forum: General Help
---

### Post by levis lover on 2010-07-11
Intalled GRUB using Live CD.
My problem is very similar to these..
```
:

1. sudo grub-install --root-directory=/mnt /dev/sda
2. sudo mount -o bind /dev /mnt/dev
3. sudo mount -t proc none /mnt/proc
4. sudo chroot /mnt
5. apt-get install grub
6. update-grub
7. exit

```
First four commands ran smoothly but the fifth one i.e.
```


apt-get install grub

```

yields this output


```
:

Err http://in.archive.ubuntu.com karmic/main grub 0.97-29ubuntu59
  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/g/grub/grub_0.97-29ubuntu59_i386.deb  Could not resolve 'in.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

Then i just restarted. 
And GRUB prompted at startup.
then i tried these commands
```

grub > find /boot/grub/stage1
grub > root(hd0,5)
grub > setup(hd0)

```
And this was the output
```

Checking if "/boot/grub/stage1" exits  Yes
checking if "/boot/grub/stage2" exists yes
checking if "/boot/grub/e2fs_stag1_5" exists yes
Running "embed /boot/grub/e2fs_stage1_5(hd0)" 17 sectors embedded succeeded
Running "install /boot/grub/stage1 (hd0) (hd0)1+17p (hd0,5) /boot/grub/stage2 /boot/grub/menu.lst" Succeeded 

```

Now every time i restart same GRUB command prompt appears. It doesn't show any entries.

---

### Post by oldfred on 2010-07-11
The chroot often needs this just before the chroot command to get internet.
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf #(may or may not be necessary to establish an internet connection)

kansasnoob's one liner with &
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

If you can boot then you need to reinstall grub from inside your booted system to see if that resolves it. Did you install grub legacy when you had grub2. They often conflict.

If you want to remove old grub and cleanly install grub2 (grub-pc)

While chrooted or from inside your booted system:

apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
apt-get install --reinstall grub-pc
grub-install /dev/sda
grub-install --recheck /dev/sda
update-grub

---

