---
title: "Eth HDD mount with read and write"
date: 2011-07-01
forum: General Help
---

### Post by al_mic on 2011-07-01
Hi,

I have this Western Digital external hard drive. 
[http://reviews.cnet.com/network-storage/western-digital-my-book/4505-3382_7-34192049.html](http://reviews.cnet.com/network-storage/western-digital-my-book/4505-3382_7-34192049.html)
I connect it to my local switch/router and I can access it through the network at some IP address.
Product specifications says that it supports Windows and Mac and indeed it does work as expected on Windows.

Of course I am using Ubuntu (11.04) on my laptop and I was trying to mount it and use it.
So far I was able to mount it and move stuff to it, but only as root user.
And this is a bit annoying because I am unable to change files on it on the fly or grab some video and drag it there.

Here is what I do to mount it:
1. create some directory in /mnt , /media or in /home/me/
2. execute this command:
sudo mount -t cifs //192.168.1.5/Public /home/me/wd -o --username=admin,password=somepass

I did searched the web for solutions about how to mount it and be able to write on those files with my normal linux user, but those commands did not worked for me.

Do you have any ideas what to do?
All I want is to mount it in a way my normal user will be allowed to write files on it (or change the ones already there)

Thank you.

---

### Post by prodigy_ on 2011-07-01
If you want to automount CIFS, you'll need to add a line to your /etc/fstab file. Assuming uid and gid of 1000 (defaults), the simplest format is:

```
//192.168.1.5/Public /home/me/wd cifs username=admin,password=somepass,uid=1000,gid=1000 0 0
```

If you don't want to automount just add **uid=1000,gid=1000** to mount command options. To check your uid/gid you can use: ```
id -u; id -g
```

More info about CIFS and more options here:
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)
and here:
[http://linux.die.net/man/8/mount.cifs](http://linux.die.net/man/8/mount.cifs)

---

### Post by al_mic on 2011-07-01
Well, that was fast... :)

Your advice was great!
Just by adding ",uid=1000,gid=1000" to my initial command I made it now work.

So the final command is:
sudo mount -t cifs //192.168.1.5/Public /home/me/wd -o --username=admin,password=somepass,uid=1000,gid=1000

I am able to write :)

Thank you!

I will try the automount at start up too, but not right now. (still enjoying the write capability) 
I am unsure about how this goes when you have no IP..
As far as I know I get my IP address from the DHCP server after I type my password to log in.
Question is if at that point the remote drive should or not be mounted.
If it should, then I guess mount operation will be unsuccessful and who knows what errors linux may throw up.

I will post a new message here after I test the /etc/fstab change.

Thanks again!

---

### Post by prodigy_ on 2011-07-01
> **al_mic said:**
> I am unsure about how this goes when you have no IP..
You can add **noauto** option (to the fstab line). Then Ubuntu won't try to mount the HDD at boot. For mounting "noauto" partitions, you can use **sudo mount -a** command (or just **mount -a** if you'll also add **users** or **user=your-username** option).

---

### Post by al_mic on 2011-07-02
I tried adding that line in /etc/fstab but it did not work.
I also set my wireless interface IP from DHCP to Static, but it still didn't work.

This is not a big problem though.
I have some bash scripts made to mount and unmount that device and I am able to execute them by sudo power with no password.

For who wants to know, this is what I did:

1. Create the 4 scripts:
$ cd /home/me/Desktop/
$ sudo mkdir mount
$ cd mount
$ sudo vim mount_wd_hdd.sh
```

#!/bin/bash -
mount -t cifs //192.168.1.5/Public /home/me/wd -o --username=admin,password=somepass,uid=1000,gid=1000

```$ sudo vim do_mount.sh
```

#!/bin/bash -
sudo /home/me/Desktop/mount/mount_wd_hdd.sh

```$ sudo vim unmount_wd_hdd.sh
```

#!/bin/bash -
umount /home/me/wd

```$ sudo vim do_un_mount.sh
```

#!/bin/bash -
sudo /home/me/Desktop/mount/unmount_wd_hdd.sh

```$ sudo chmod +x *

2. Change sudo access rights for my user:
$ sudo visudo
- at the top of the file, after the line with "Defaults        env_reset" make sure to have this:
```

Defaults        env_reset
Defaults:me runas_default=root

```- ^ me is my username here

- at the bottom of the file, after the lines with
"%admin ALL=(ALL) ALL"
and
"%sudo   ALL=(ALL:ALL) ALL"
make sure to have this:
```

me ALL=NOPASSWD: /home/me/Desktop/mount/mount_wd_hdd.sh, /home/me/Desktop/mount/unmount_wd_hdd.sh

```- again, ^ me is my username

Then all I have to do is to open that directory on my desktop and double click on do_mount.sh
and choose Run in Terminal


I do have one small problem though with all these.
If I try to restart my computer without unmounting the drive first, it hangs..
Seems that it is not able to unmount it by itself. Even if I have no open files from there.

To avoid this problem I must remember to execute the unmount operation before restart or shut down. 
But I am sure this is not the fix.
Must be something that can be done to make it (my linux) able to unmount it by itself.

I tried placing a script in /etc/rc6.d/ and /etc/rc0.d/ right before S31umountnfs.sh.
Called it S31aaa-umount-wd-hdd  :)
But it still hangs...

---

### Post by prodigy_ on 2011-07-02
> **al_mic said:**
> I tried adding that line in /etc/fstab but it did not work.
I also set my wireless interface IP from DHCP to Static, but it still didn't work.
Very strange. What error do you get?

> 
I do have one small problem though with all these.
If I try to restart my computer without unmounting the drive first, it hangs.
Seems to be this bug:
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/211631](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/211631)

---

### Post by al_mic on 2011-07-02
Being unable to automount it with /etc/fstab was just me being silly.
I typed to wrong IP address in the fstab line.

But now that I have the correct addres:
```

//192.168.1.5/Public /home/me/wd cifs username=admin,password=somepass,uid=1000,gid=1000 0 0

```
it mount itself at start up. :)

I must say that is does not do that from the first try.
I get these errors at boot:

```

kernel: [   23.274074] CIFS VFS: Error connecting to socket. Aborting operation
kernel: [   23.274086] CIFS VFS: cifs_mount failed w/return code = -101

kernel: [   24.607910] CIFS VFS: Error connecting to socket. Aborting operation
kernel: [   24.607918] CIFS VFS: cifs_mount failed w/return code = -101

```

But it works.. 
Maybe they are because the network is still not up.
As I said I now have my wireless network interface set to a static IP.


As for the reboot/shutdown part... well, it still does not work. (I will use my unmount script)
I believe the bug from the link you gave me is the one affecting me too.
I will just have to wait for Ubuntu to fix it..

Just as an extra info, this is the error that I get at reboot.
- it hangs and if I press ctrl+alt+del I get:
```

unable to connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused 
init: plymouth-upstart-bridge main process (2315) terminated with status 1

```

Thank you for helping me so far.

---

### Post by prodigy_ on 2011-07-02
> **al_mic said:**
> I tried placing a script in /etc/rc6.d/ and /etc/rc0.d/ right before S31umountnfs.sh.
Called it S31aaa-umount-wd-hdd  :)
But it still hangs...
S31umountnfs.sh already tries to unmbout CIFS but apparently it's too late.

You can try to call **/etc/init.d/umountnfs.sh** from **/etc/gdm/PostSession/Default**. Not sure if it'll work but worth a shot.

---

### Post by al_mic on 2011-07-04
I tried placing that line in /etc/gdm/PostSession/Default but it did not work. (still hangs)
But thanks.

I will unmounting manually before shutdown. (almost manually.. I have that script..)

---

