---
title: "Press C to continue to wait; or press S to skip mounting or M for manual recovery"
date: 2011-03-23
forum: General Help
---

### Post by al111 on 2011-03-23
I'm randomly getting *'Continue to wait; or press S to skip mounting or M for manual recovery...'* or something like that at boot ((it flashes very quickly)- 

If I don't press anything, I'm prompted for my password (I configured it to login with password) and the desktop loads...

I'm using Ultimate Edition 2.6.1 -> [Ultimate Edition Home]("http://forumubuntusoftware.info/")

I was using my 1TB hdd to dual-boot linux, windows, and for storage...

Yesterday, I imaged the linux partition, and restored it to an approximately 66GB partition I created on a 150GB hdd...

Besides the 66GB partition, the rest of the 150GB hdd is 'unallocated space'...

That's when the above message started...

Below are screenshots of the fstab and partitions as they are now...

Any help getting this fixed is appreciated...

[IMG]http://i390.photobucket.com/albums/oo347/bubba9191/fstab.jpg[/IMG]

[IMG]http://i390.photobucket.com/albums/oo347/bubba9191/fdisk.jpg[/IMG]

EDIT:  added gparted image

[IMG]http://i390.photobucket.com/albums/oo347/bubba9191/gparted-1.jpg[/IMG]

---

### Post by al111 on 2011-03-23
bump

---

### Post by Krytarik on 2011-03-23
Did you update the UUIDs after moving to the new drive?

Check them with
```
sudo blkid
```
and update "/etc/fstab" and "/etc/initramfs-tools/conf.d/resume" accordingly.
[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

Greetings.

---

### Post by al111 on 2011-03-24
> **Krytarik said:**
> Did you update the UUIDs after moving to the new drive?

Check them with
```
sudo blkid
```
and update "/etc/fstab" and "/etc/initramfs-tools/conf.d/resume" accordingly.
[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

Greetings.

I will thanks-

---

### Post by al111 on 2011-03-24
I checked, but I don't know what I'm looking at, or what needs to be corrected or updated...

Looks to me like the swap UUID is either wrong or is missing...

Very no0b here-

[IMG]http://i390.photobucket.com/albums/oo347/bubba9191/UUID.jpg[/IMG]

---

### Post by Krytarik on 2011-03-24
The swap partition seems indeed to be the cause of the issue, because its UUID is indeed missing, and its entry in "fstab" is therefore incorrect. Because of this its mounting at boot fails. But the UUID of your root partition in "fstab" is correct.

You could simply replace the UUID of the swap partition's entry in "fstab" with "/dev/sda5", but I'd prefer to use its UUID instead, therefore of course it needs to be set first, we will simply format it therefore:

- format it by using GParted
- lookup its (hopefully now set) UUID with "sudo blkid"
- update "/etc/fstab" and "/etc/initramfs-tools/conf.d/resume" accordingly

---

### Post by al111 on 2011-03-24
Okay, I deleted the old swap file and partition, and created a new one...

I updated '/etc/fstab' with new UUID...

I updated '/etc/initramfs-tools/conf.d/resume' with new UUID as per directions @ [https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

When I updated '...conf.d/resume', I added '*_UUID*' at the end...I typed:

```

RESUME=UUID=b4115e32-9d8e-401b-8917-71e467de3d7f_UUID

```

and saved...does it look okay?

Thanks!!!!

[IMG]http://i390.photobucket.com/albums/oo347/bubba9191/B_gparted.jpg[/IMG]

[IMG]http://i390.photobucket.com/albums/oo347/bubba9191/A_blkid.jpg[/IMG]

[IMG]http://i390.photobucket.com/albums/oo347/bubba9191/C_fstab.jpg[/IMG]

[IMG]http://i390.photobucket.com/albums/oo347/bubba9191/D_resume.jpg[/IMG]

---

### Post by Krytarik on 2011-03-24
> **al111 said:**
> 
When I updated '...conf.d/resume', I added '*_UUID*' at the end...I typed:
```

RESUME=UUID=b4115e32-9d8e-401b-8917-71e467de3d7f[COLOR=Red]**_UUID**[/COLOR]

```and saved...does it look okay?Aside from that you need to remove the "_UUID" part ;-), and assuming that you took the lower most screenshot before updating it, everything seems fine.

---

### Post by al111 on 2011-03-24
> **Krytarik said:**
> Aside from that you need to remove the "_UUID" part ;-), and assuming that you took the lower most screenshot before updating it, everything seems fine.

Actually I took the lowermost screenshot (in post # 7) *after* I updated it....

But I just edited it again, removing *'_UUID'*, then I entered in terminal:

```

sudo update-initramfs -u

```

...and took this screenshot-

[IMG]http://i390.photobucket.com/albums/oo347/bubba9191/resume_final.jpg[/IMG]

That should do it??

---

### Post by Krytarik on 2011-03-24
> **al111 said:**
> Actually I took the lowermost screenshot (in post # 7) *after* I updated it....

Then at least you run the first command before updating "resume".

Anyway, everything seems alright now, then just dare a reboot!

---

### Post by al111 on 2011-03-24
> **Krytarik said:**
> Then at least you run the first command before updating "resume".

Anyway, everything seems alright now, then just dare a reboot!

I booted it twice, the first time at the top of the splash screen it said 

*'keys: Press C to cancel all checks currently in progress'*

The second time it was gone...

Seem okay??

---

### Post by Krytarik on 2011-03-24
> **al111 said:**
> I booted it twice, the first time at the top of the splash screen it said 

*'keys: Press C to cancel all checks currently in progress'*

The second time it was gone...

Seem okay??
Yeah, seems ok. That was just a routine check of *any* filesystem, I believe of your root partition, because the swap partition is not marked for routine checks, maybe just coincidence.

---

### Post by al111 on 2011-03-24
> **Krytarik said:**
> Yeah, seems ok. That was just a routine check of *any* filesystem, I believe of your root partition, because the swap partition is not marked for routine checks, maybe just coincidence.

I'll mark this thread 'SOLVED'...

Thanks!

---

