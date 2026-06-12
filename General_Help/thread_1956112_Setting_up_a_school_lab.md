---
title: "Setting up a school lab"
date: 2012-04-10
forum: General Help
---

### Post by Sternfan on 2012-04-10
Hi all,
I currently have a lab of 12 XP PCs that are shared by students (their "fun" lab) that I would like to convert to Ubuntu.  The students use the lab for surfing the internet, playing music (MP3s in their music folder) and some installed games.  In the past there has been vandalism issues with the OS (changing the background, posting notes to the desktop, changing homepage, changing browser settings to avoid the squid cache etc).  

I solved this by creating a single account, configuring it as necessary in Group Policy and making it a "mandatory roaming profile."  In short, they can try to change anything but those changes will not be saved.  The next user logs in - they get a clean user account.

I was thinking of a kiosk - but everything I find has just the browser - no access to the MP3s or games.

I also thought of using Pessulus to lock everything down, but that doesn't address things like how do all the students share the same home folder (music)?

I also looked at edubuntu but the only server I have is a bit older - only two CPUs (not even dual core) and 2gb ram (though it can take 8gb) - so not sure if going this route is worth the effort.

Any idea on how to do this with Ubuntu?  If anyone out there has done something similar, I am curious as to how you did it.

Thanks,
Rob

---

### Post by roelforg on 2012-04-10
Are the pc's identical in hd?
If so,
you can use ubuntu server and create a standard disk image for the clients.
Or if your network is fast enough with enough bandwidth, you could do a netboot.

Also,
Do the pc's support PXE-boot and are on the same switch as the switch?
If so, you could have the server be the router and every pc can PXEboot pxelinux,
make 2 configs for pxelinux: 1 for boot from hd, 1 for boot from nfs.
Then you can create a nfsboot distro (i can do that for you) that will dd the image to the hd, that way, if you update the image you can switch config from local to nfs and have the auto-installer run and shut down the pc, reboot every single pc, then switch config again.

The disk image can be done very easy.
If you can get your way around the cli, that is.
Create a kickstart iso from the standard ubuntu iso that has root enabled (modify the ubuntu server one as well to have root as well).
Create an image the size of the hd's.
Use qemu to have the modified desktop iso install on the image.
That image is the new hd-image.
Every time you need to modify the image,
you can:
 * Use qemu to boot it and modify it that way.
 * Chroot in to it and mount /proc

Now to share the data over multiple machines
Mount the image and move the /home of the image to a NFS shared dir (not in the image).
Make an empty dir in the nfsshare that will hold common configs.
The most important are /etc/passwd /etc/shadow and /etc/group
Make an empty dir in the image for /home and /sharedconf.
Modify the images /etc/fstab to mount /home and /sharedconf as nfs.
Chroot (as root) to the image (procedure can be found online, but mount /sys /dev and /proc)
mount the shared conf dir manually.
Move the /etc/passwd /etc/shadow /etc/group files to the /sharedconf (the shared config dir) dir and symlink them.
Now you should be able to install the image and it will mount the /home dirs and the shared password and group files!
Now just read up on file/dir permissions and the like to design and implement good permissions so that every student can read his/her own home dir but no-one else's.

And done.

---

### Post by SeijiSensei on 2012-04-10
Take a look at [LTSP]("http://www.ltsp.org/") as an option.  

There also used to be a commercial program that would restore the PC to a standard image upon each reboot.  I can't remember what it's called and can't seem to find it via Google.  Maybe someone else here remembers what it is.

---

### Post by roelforg on 2012-04-10
> **SeijiSensei said:**
> Take a look at [LTSP]("http://www.ltsp.org/") as an option.  

There also used to be a commercial program that would restore the PC to a standard image upon each reboot.  I can't remember what it's called and can't seem to find it via Google.  Maybe someone else here remembers what it is.

Dunno,
but it ain't to hard to use debootstrap to create a (minimal) nfsbooting system who's only purpose is to run
```

dd if=/path/to/shared/image.img of=/dev/sda
poweroff

```
And use pxe with 2 configs (1 for local hd boot and 1 for nfs boot),
and just swap the configs and reboot the client when a system needs an reimage, and swap them back afterwards.
Easy, no?

---

