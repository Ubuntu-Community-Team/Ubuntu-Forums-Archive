---
title: "How to Undo GRUB edit."
date: 2011-02-23
forum: General Help
---

### Post by Uthallan on 2011-02-23
Hello,

  I recently had to edit my GRUB in order to fix a problem I had with my Nvidia graphics card causing a black screen after install, but now I cannot boot from my live CD. When I try nothing happens as if there wasn't even a CD in the drive. I was able to boot from the CD just fine before I edited my GRUB. My question is how do I reset GRUB back to the way it was by default so I can see if it fixes my boot problem?


For reference my GRUB now looks like this:


recordfail
insmod part-msdos
insmod ext2
set root='(hdo,msdos1)'
Search --no-floppy --fs-uuid --set 329b8dbf-d45f-4b51-bff9-3b661a45d\
f46
linux /boot/vmlinuz-2.6.35-25-generic root=UUID=329b8dbf-d45f-4b51-b\
ff9-3b661a45df46 ro quiet splash
initrd /boot/initrd.img-2.6.35-25-generic

---

### Post by drs305 on 2011-02-23
For starters, this:
> set root='(hdo,msdos1)'
should probably look like this (a zero, not a lowercase O):
> set root='(hd0,msdos1)'

However, it's the BIOS that determines if you are going to boot the CD first. Make sure it designates the CD drive as the first to boot, and then listen for the CD to spin up to see if the BIOS is indeed attempting to boot the CD.

---

### Post by Uthallan on 2011-02-23
The CD does spin, and everything seems to be happening, until it doesn't. I just get a normal boot into my desktop.

and the GRUB I posted was from a handwritten copy I made because It's on the same machine i'm using to post, so I didn't know how else to get it here. small things like that should be as normal. the line I edited was:

linux /boot/vmlinuz-2.6.35-25-generic root=UUID=329b8dbf-d45f-4b51-b\
ff9-3b661a45df46 ro quiet splash

Whatever was there before is what I replaced with this.

---

### Post by stchman on 2011-02-23
I have never found a need to edit GRUB's .conf file.  Install StartUpManager.

```

sudo apt-get install startupmanager

```

This allows you to make GRUB changes safely.

---

### Post by drs305 on 2011-02-23
> **Uthallan said:**
> The CD does spin, and everything seems to be happening, until it doesn't. I just get a normal boot into my desktop.

I'm a little confused about your boot. Are you saying you can boot to your normal Ubuntu but just cannot get the CD to boot?

If you can boot to your normal Ubuntu installation, and you edited the /boot/grub/grub.cfg file, all you have to do is run the following to rebuild grub.cfg:
```
sudo update-grub
```

If you edited /etc/default/grub, and want to get it back to default:
From a normal Ubuntu boot:
```

sudo cp /usr/share/grub/default/grub /etc/default/
sudo update-grub
```

If your LiveCD doesn't boot and you have another bootable CD of any type you might try it to see if the replacement boots. If the second CD boots it could be your LiveCD became damaged somehow.

---

### Post by Uthallan on 2011-02-23
I know how to edit GRUB, what I don't know is what to Edit it back to in order to make it like it was before I changed it, or if I even need to.

---

### Post by Uthallan on 2011-02-23
> **drs305 said:**
> I'm a little confused about your boot. Are you saying you can boot to your normal Ubuntu but just cannot get the CD to boot?

If you can boot to your normal Ubuntu installation, and you edited the /boot/grub/grub.cfg file, all you have to do is run the following to rebuild grub.cfg:
```
sudo update-grub
```

If you edited /etc/default/grub, and want to get it back to default:
From a normal Ubuntu boot:
```

sudo cp /usr/share/grub/default/grub /etc/default/
sudo update-grub
```

If your LiveCD doesn't boot and you have another bootable CD of any type you might try it to see if the replacement boots. If the second CD boots it could be your LiveCD became damaged somehow.

Yes I can boot to my normal Ubuntu, but just cannot get the live CD to boot. I am able to boot from a Vista CD that I have, but I see no reason to think that the CD is damaged in any way. I will try to make a new one and boot from it just to see what happens though.

---

### Post by drs305 on 2011-02-23
> **Uthallan said:**
> Yes I can boot to my normal Ubuntu, but just cannot get the live CD to boot. I am able to boot from a Vista CD that I have, but I see no reason to think that the CD is damaged in any way. I will try to make a new one and boot from it just to see what happens though.

Yes, trying a new CD may work. 

Unless you are trying to boot an ISO from the Grub 2 menu, by the time Grub comes into the boot process the opportunity to boot a CD is past - at least if you want to boot an operating system. That is handled by BIOS, which directs which device to look at for booting instructions. 

If you are trying to get a CD to run within Ubuntu, that also isn't controlled by Grub 2.

---

### Post by Uthallan on 2011-02-23
> **drs305 said:**
> Yes, trying a new CD may work. 

Unless you are trying to boot an ISO from the Grub 2 menu, by the time Grub comes into the boot process the opportunity to boot a CD is past - at least if you want to boot an operating system. That is handled by BIOS, which directs which device to look at for booting instructions. 

If you are trying to get a CD to run within Ubuntu, that also isn't controlled by Grub 2.

No luck with a freshly burned DVD-R, and now I can't even boot up a windows 7 CD. Something wrong with BIOS maybe?

---

