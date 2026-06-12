---
title: "Used /dev/sda1 as a mount location; strange non-removable drive in my &quot;Places&quot;"
date: 2009-11-22
forum: General Help
---

### Post by Treeh on 2009-11-22
Hello,

I modified /etc/fstab with the following line:

```

UUID="AA6638EB6638BA41" /dev/sda1 ntfs-3g ro,auto,user,fmask=0111,dmask=0000 0 0 
```

The mount, of course, did not work and I quickly realized mounting to /dev/sda1 was idiotic. I changed it to /media/media and it works fine now.

However, now I have a remnant drive in my "Places" menu that simply leads to this error when I click on it (it's highlighted, its functioning counter-part is the "Media" one):

[IMG]http://i.imgur.com/5zH6P.png[/IMG]

Does anyone have any idea how I can remove the drive from the Places menu?

---

### Post by lswb on 2009-11-22
Do you actually have a /media/media directory?

---

### Post by Treeh on 2009-11-22
> **lswb said:**
> Do you actually have a /media/media directory?

Yes, I created it. The drive itself works fine, it's just that because I tried to mount in /dev/sda1, I'm left over with the non-functioning "link" to the drive in my Places menu. Even when I unmount the drive.

This isn't a question of functionality--I simply want to remove the "link" from my Places menu.

---

### Post by Treeh on 2009-11-23
Bumpidy!

---

### Post by Treeh on 2009-11-24
> **Treeh said:**
> Bumpidy!

...and again.

---

### Post by ricardo.gloe on 2009-11-24
your fstab line is pointing to /media/media? or /media/Media?

I had a similar problem by creating a mount point named /media/bkp but my HD label was BKP, and I ended up with both in Places.

Have you tried removing all modifications, checking /media for any leftover folders/directories and deleting them, and then after rebooting, edit you ftstab correctly? That's what I did.

I noticed you said you created the /media/media folder. That's pretty much what I did also. Try the above, it worked for me (I don't think you have to create any folder in /media, just edit the fstab line)

---

### Post by QLee on 2009-11-24
Treeh,
What is the label of the "drive" (partition) in question. Is it perhaps "Media"?

You can see the label; UUID; and device node for partitions with the command sudo blkid. (That will give those things in all partitions on you system, probably sudo blkid /dev/sda1 will give the answer you need.)

---

### Post by dcstar on 2009-11-25
> **Treeh said:**
> 
.......
Does anyone have any idea how I can remove the drive from the Places menu?

Apart from right-clicking the entry and selecting "Remove"?

---

### Post by Treeh on 2009-11-26
> **dcstar said:**
> Apart from right-clicking the entry and selecting "Remove"?

It's "blanked-out".

---

