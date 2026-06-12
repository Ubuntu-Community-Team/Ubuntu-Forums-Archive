---
title: "changin /home"
date: 2011-06-12
forum: General Help
---

### Post by devonte on 2011-06-12
I tried to change my /home to another partition, but after reboot I get an error saying the disk /home could not be mounted..

fstab:


> 

e# /etc/fstab: static file system information. # # Use 'blkid -o value -s UUID' to print the universally unique identifier # for a device; this may be used with UUID= as a more robust way to name # devices that works even if disks are added and removed. See fstab(5). # # <file system> <mount point>   <type>  <options>       <dump>  <pass> proc            /proc           proc    nodev,noexec,nosuid 0       0 # / was on /dev/sda5 during installation UUID=6d6eb191-28ed-42f2-bbd8-be010ba53956 /               ext4    errors=remount-ro 0       1 # swap was on /dev/sda6 during installation UUID=8affa174-ae4e-416c-9030-b4df7fe23066 none            swap    sw              0       0  # /dev/sda1 UUID="d8548b81-177a-41a1-a7a6-1f9b79e4eb57 /home   ext4    defaults 1 2



---

### Post by pqwoerituytrueiwoq on 2011-06-12
can you post your fstab file?
located in the etc folder

you did remember to update the fstab file right?
after moving you may need to fix the permissions to the home folder

---

### Post by prodigy_ on 2011-06-12
> **devonte said:**
> I tried to change my /home to another partition
What do you mean? What exactly did you do?

> fstab:
Err. Not readable. (Or if your fstab actually looks like this, the system probably won't even boot.)

Normally fstab should look like this (I omitted all lines starting with # as they are comments and can be ignored):
```
proc    /proc    proc    nodev,noexec,nosuid    0    0
UUID=7a88069a-dd98-4dc0-b128-3e8c2e3d490a    /    ext4    relatime, errors=remount-ro    0    1
UUID=4d916ad3-a862-4ab0-9383-433d03654026    none    swap    sw    0    0
```
It can have more lines and actual device paths like **/dev/sda1** can be used instead of UUIDs, but the idea is still the same - one filesystem per line.

So...

Can you please post the output of the following commands:
```
cat /etc/fstab
cat /etc/mtab
```

---

### Post by Morbius1 on 2011-06-12
He actually did post his fstab but it must have been in "tweat format" ;) :
> proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda5 during installation
UUID=6d6eb191-28ed-42f2-bbd8-be010ba53956 / ext4 errors=remount-ro 0 1
# swap was on /dev/sda6 during installation
UUID=8affa174-ae4e-416c-9030-b4df7fe23066 none swap sw 0 0
# /dev/sda1 UUID="d8548b81-177a-41a1-a7a6-1f9b79e4eb57 /home ext4 defaults 1 2I'm assuming You put the "#" on the last line so you could boot. It has the wrong syntax for one thing. It should be something like this:
```
UUID=d8548b81-177a-41a1-a7a6-1f9b79e4eb57 /home ext4 defaults 1 2
```You also might want to run the following command to make sure you have the correct uuid number:
```
sudo blkid -c /dev/null
```

---

