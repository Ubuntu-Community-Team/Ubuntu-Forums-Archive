---
title: "trying to add ram disk to fstab but fstab fails to boot"
date: 2010-05-26
forum: General Help
---

### Post by oarion7 on 2010-05-26
Hi there.

I was able to succesfully create a small, fixed-size "ram disk" just for kicks, via:

```
sudo mkfs -t ext3 -q /dev/ram1 65536
sudo mkdir -p /media/ramdisk
sudo mount /dev/ram1 /media/ramdisk -o defaults,rw
```

However, I wanted it to auto-boot, so I added the line to fstab:

```
/dev/ram1       /media/ramdisk ext3 defaults 0 0
```

This, however, rendered Ubuntu unbootable and I had to repair the fstab by removing the line via a Live CD. I had enough patience to boot through the CD an extra time to see if just deleting "ext3" would work, but it did not.

What would cause this to make the system unbootable and could anyone help me as to how I could make it work?

Thanks

---

### Post by john newbuntu on 2010-05-26
I had similar problems a while back.  Try using the upstart mechanism or the good old system5 init method to mount the ramdisk.  Basically stick the commands that you have listed in the first code block(without the sudo) in /etc/rc.local.  Also add a chown and chmod commands towards the end appropriately.

---

### Post by stinger30au on 2010-05-27
why bother when ubuntu has a ramdisk built in by default

its location is

/dev/shm

---

### Post by jocko on 2010-05-27
> **oarion7 said:**
> Hi there.

I was able to succesfully create a small, fixed-size "ram disk" just for kicks, via:

```
sudo mkfs -t ext3 -q /dev/ram1 65536
sudo mkdir -p /media/ramdisk
sudo mount /dev/ram1 /media/ramdisk -o defaults,rw
```However, I wanted it to auto-boot, so I added the line to fstab:

```
/dev/ram1       /media/ramdisk ext3 defaults 0 0
```This, however, rendered Ubuntu unbootable and I had to repair the fstab by removing the line via a Live CD. I had enough patience to boot through the CD an extra time to see if just deleting "ext3" would work, but it did not.

What would cause this to make the system unbootable and could anyone help me as to how I could make it work?

Thanks
The reason it fails is because when you reboot the ramdisk is gone. You need to create it before it is supposed to be mounted (every boot).
But, as already been pointed out, ubuntu already have a ramdisk in /dev/shm. Either use that one, or if you want to make another one, make the fstab line look like this:
```
tmpfs /media/ramdisk tmpfs defaults 0 0
```That way the ramdisk will be created when it's mounted.

---

### Post by oarion7 on 2010-05-27
> **john newbuntu said:**
> I had similar problems a while back.  Try using the upstart mechanism or the good old system5 init method to mount the ramdisk.  Basically stick the commands that you have listed in the first code block(without the sudo) in /etc/rc.local.  Also add a chown and chmod commands towards the end appropriately.

This worked perfectly, thanks! That's a handy script I didn't know exists.

> **stinger30au said:**
> why bother when ubuntu has a ramdisk built in by default

its location is

/dev/shm
> **jocko said:**
> The reason it fails is because when you reboot the ramdisk is gone. You need to create it before it is supposed to be mounted (every boot).
But, as already been pointed out, ubuntu already have a ramdisk in /dev/shm. Either use that one, or if you want to make another one, make the fstab line look like this:
```
tmpfs /media/ramdisk tmpfs defaults 0 0
```That way the ramdisk will be created when it's mounted.

Thank you both, I'll remember this for the future. For this time I wanted to experiment with creating a fixed-size RAM disk, rather than a dynamic one.

Thank you all!

---

### Post by john newbuntu on 2010-05-27
@Oarion7:  Glad it worked.  But isn't ramdisk really dynamic always but limits to your available RAM?

@stinger30au: Is /dev/shm really a ramdisk? I was under the impression that it was a tmpfs which is different from a ramfs.

@jocko: The command that you gave mounts it as tmpfs.  Should the type be ramfs in order to mount it as a ramdisk?  Sorry I have not tried this but was curious.

---

