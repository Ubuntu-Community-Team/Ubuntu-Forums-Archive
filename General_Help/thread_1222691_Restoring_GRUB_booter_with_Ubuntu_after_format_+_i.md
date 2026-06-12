---
title: "Restoring GRUB booter with Ubuntu after format + install of Windows 7 on NTFS"
date: 2009-07-25
forum: General Help
---

### Post by szenith on 2009-07-25
*****I MOSTLY SOLVED THIS, BUT HAVE ANOTHER PROBLEM, WITH MOUNTING MY NTFS DRIVE IN UBUNTU!! SCROLL DOWN TO SEE!! :)*****

Okay, so I reinstalled GRUB after installing Windows 7 RC on an NTFS partition I formatted with it's installer. I have GRUB installed now and am able to boot into Ubuntu which I have installed on an ext3 partition, but I can't boot into Windows 7 from the default GRUB screen, selecting the default Windows menu option added by the GRUB installer doesn't work, it just brings me back to the menu screen. I am not very good with editing GRUB, so I need help..

Here is the fdisk -l info on my devices:
```
ivan@ivan-desktop:~$ sudo fdisk -l
[sudo] password for ivan: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd629d629

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       55937   449313921    7  HPFS/NTFS
/dev/sda2           55938       60801    39070080    5  Extended
/dev/sda5           55938       60596    37423386   83  Linux
/dev/sda6           60597       60801     1646631   82  Linux swap / Solaris

```

Here's the entirety of my GRUB file in /boot/grub/menu.lst on pastebin: [http://pastebin.com/m654b9d93](http://pastebin.com/m654b9d93)

So if anyone could help me, that would be great, thank you!

---

### Post by DeMus on 2009-07-25
> **szenith said:**
> Okay, so I reinstalled GRUB after installing Windows 7 RC on an NTFS partition I formatted with it's installer. I have GRUB installed now and am able to boot into Ubuntu which I have installed on an ext3 partition, but I can't boot into Windows 7 from the default GRUB screen, selecting the default Windows menu option added by the GRUB installer doesn't work, it just brings me back to the menu screen. I am not very good with editing GRUB, so I need help..

Here is the fdisk -l info on my devices:
```
ivan@ivan-desktop:~$ sudo fdisk -l
[sudo] password for ivan: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd629d629

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       55937   449313921    7  HPFS/NTFS
/dev/sda2           55938       60801    39070080    5  Extended
/dev/sda5           55938       60596    37423386   83  Linux
/dev/sda6           60597       60801     1646631   82  Linux swap / Solaris

```

Here's the entirety of my GRUB file in /boot/grub/menu.lst on pastebin: [http://pastebin.com/m654b9d93](http://pastebin.com/m654b9d93)

So if anyone could help me, that would be great, thank you!

You write about Windows 7. In your menu.lst file it says
Title: Microsoft Windows XP Professional.
How come?

---

### Post by szenith on 2009-07-25
> **DeMus said:**
> You write about Windows 7. In your menu.lst file it says
Title: Microsoft Windows XP Professional.
How come?

because that's what the GRUB installer installs it as, I changed it to say "Windows 7" but it's just the description, it doesn't change any of the actual boot info, I reverted because I had changed something else as well to see if it would let me boot into it but it didn't. I didn't bother changing it back to Windows 7 just so I could emphasize that I have the original grub menu file installed. I will change it to again say Windows 7, but that doesn't change whether it's bootable or not, I mean I could put anything as the name, it's just a description.

---

### Post by szenith on 2009-07-25
******KEEP SCROLLING TO MY NEXT POST TO SEE THE CURRENT PROBLEM I AM DEALING WITH******

I have another problem now: I'm unable to mount my NTFS partition in Ubuntu, it doesn't even see it. The Ubuntu LIVE CD saw the NTFS partition though, I checked when I was reinstalling GRUB through it. 

Now it gives me this error message when i try to mount it:

```
ivan@ivan-desktop:~$ sudo mount /dev/sda1
Unexpected clusters per mft record (-1).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```

When I was installing GRUB I manged to remount it to /media/root by typing

mount /dev/sda1 /media/root/boot

but then mounted my Ubuntu partition to /media/root/boot (which was sda5) and installed GRUB there instead

also when I was installing GRUB from the LIVE CD I typed

sudo grub-install --root-directory=/media/root /dev/sda

AND 

sudo grub-install --root-directory=/media/root /dev/sda1

and then I think I did 

sudo grub-install --root-directory=/media/root /dev/sda5

to actually install it on linux, but I'm not entirely sure, but I think I needed to do that for it to work?

anyway, I was unsure exactly how to do it. So, but now I'm in my regular Ubuntu boot and I can't seem to get into my NTFS partition from it, and the LIVE CD doesn't see it either anymore for some reason.. I haven't managed to boot into Windows 7 at all since I got back into Ubuntu through GRUB, when I select it on the prompt it says Loading GRUB 2.0 or something like that, and takes me back to the boot menu (the first time GRUB loads it says GRUB 1.5). Anyway this is kind of weird, help would be appreciated!

---

### Post by szenith on 2009-07-25
OKAY, ANOTHER UPDATE:

Running the Windows 7 DVD I was able to "repair boot" or whatever and now Windows 7 loads fine from GRUB at least for now. My Ubuntu now seems to see my 460GB drive but when I try to mount it, it says "You are not privileged to mount this volume."

Is that because I mounted it as to root at one point with the live CD? Something with the permissions? Anyway I'm not sure exactly how to fix that. Help would be appreciated...

---

### Post by szenith on 2009-07-25
OKAY, ANOTHER UPDATE:

Running the Windows 7 DVD I was able to "repair boot" or whatever and now Windows 7 loads fine from GRUB at least for now. My Ubuntu now seems to see my 460GB drive but when I try to mount it, it says "You are not privileged to mount this volume."

I can mount it typing sudo mount -t ntfs-3g /dev/sda1 /media/sda1 but I want to be able to mount it on startup/from nautilus, how do I do this? Something with the permissions only let me mount it as sudo (root)!

---

### Post by merlinus on 2009-07-25
The easiest solution is to install ntfs-config

```
sudo apt-get install ntfs-config
```

Restart, and look for it in Applications/System Tools.  Type in a mountpoint, tick the appropriate boxes, and you should be good to go.

---

### Post by szenith on 2009-07-25
> **merlinus said:**
> The easiest solution is to install ntfs-config

```
sudo apt-get install ntfs-config
```

Restart, and look for it in Applications/System Tools.  Type in a mountpoint, tick the appropriate boxes, and you should be good to go.

Yeah I got this program, but it won't load..

there are two checkboxes it lets me check before it tries to load

[ ] Enable write support for internal device

[ ] Enable write support for external device

Clicking both, nothing loads

Clicking the first one it says:
```
Mounting /media/disk failed.

fuse: failed to access mountpoint / media/disk: No such file or directory
```

Clicking just the second box it also doesn't load anything..

I am not able to mount the hard drive with regular click/mount commands, only when I type 

sudo mount -t ntfs-3g /dev/sda1 /media/sda1

does it mount...

---

### Post by merlinus on 2009-07-25
Try adding this to the end of /etc/fstab:

/dev/sda1 /media/sda1 ntfs-3g defaults,locale=en_US.utf8 0 0 
and restart.

---

### Post by szenith on 2009-07-25
> **merlinus said:**
> Try adding this to the end of /etc/fstab:

/dev/sda1 /media/sda1 ntfs-3g defaults,locale=en_US.utf8 0 0 
and restart.

That worked, it's mounted on startup now, but strangely I can only mount/unmount it as root.

[IMG]http://i29.tinypic.com/2zjj8cy.png[/IMG]

I'm wondering, maybe it's because of how I mounted it on the LIVE CD, as root.. but anyway, how do I make it so I can mount/unmount the hard drive regularly logged in?

---

### Post by merlinus on 2009-07-25
Unmount the drive and then try this:

```
sudo chown -R username:username /media/sda1
```

Change username to your own.

---

