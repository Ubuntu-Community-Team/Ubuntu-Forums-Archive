---
title: "installing windows (after ubuntu)"
date: 2006-04-11
forum: General Help
---

### Post by twopeak on 2006-04-11
Hey
I have ubuntu on my computer and i will probably need to install windows too.
Is there any way i can achieve to have a dual boot system, without having to remove my -already configured- ubuntu?

I have an external disk i could use for installing windows and then get both back together?

---

### Post by jkeyes0 on 2006-04-11
I have a really awkward configuration with my home computer.
Ubuntu on primary IDE drive, Windows on my primary SATA drive (with appropriate boot loaders on each).
When I want to boot Ubuntu, i go into the BIOS and set my IDE to be the first boot device (above the SATA drive), and when I want windows, I set the SATA to first boot. 
This accomplishes a dual-boot without having to fight with boot loaders so much, and without having to reinstall ubuntu. (not the best solution, mind you, but it does get the job done...)

---

### Post by alamba on 2006-04-11
Just install win on a seperate partition and then use ubuntu live cd to reinstall grub. Just make sure you note the boot partition, etc. from your current grub.

A

---

### Post by tmahmood on 2006-04-11
If you have a Live CD(Ubuntu Live CD would be a good choice) then you can bring back your Ubuntu without Reinstalling it. Just boot with the live CD. It should detect all your partitions and say your Ubuntu partition is on hda5 and IS mounted, if live CD has detected everything then your partition should be at ```
/media/hda5
```

now do this

```

chroot /media/hda5

```

this will put you into you installed system any change you make will be applyed to you installed system

now reinstall grub using 

```
grub-install /dev/hda
```

you'll have your grub boot loader back

---

### Post by twopeak on 2006-04-11
Thanks. I'll print all this and i'll see when i install windows.
I plan to disconnect the disk with ubuntu during the windows-install, just to make sure Windows doesn't do something stupid with it.

---

### Post by twopeak on 2006-04-13
Hello

I don't have a ubuntu live cd, nor a cd-writer, but i found a (pretty) old knoppix disk (knoppix 3.4).
If I use that, I had some trouble finding my disks, i finally found them in /mnt/hda1
When I try chroot /mnt/hda1 it tells me the operation is not permited
When I try sudo chroot /mnt/hda1 it tells me that /mnt/hda1 is not a dir.

I tried while being in that dir and while not being in that dir...

Is there no way to do this otherwise? Or with my normal Ubuntu (it does recognize the windows disk after all) or using an external usb harddisk?
Thank you

[edit]On default, Grub is still starting, and Windows never appears, I just see the disc once ubuntu started.

---

### Post by petri on 2006-04-13
But you have the Ubuntu installation CD?

Here you find a [howto]("http://ubuntuforums.org/showthread.php?t=76652&highlight=howto+install+grub") install grub with the installation cd.

And [here]("http://www.gnu.org/software/grub/manual/grub.html#Stage2-errors") you find error codes to grub. Just in case ;)

---

### Post by andy_cowman on 2006-04-13
Hi

Depending on what you are using windows for and how powerful your PC is you could try VMPlayer with XP installed through that. Then you can move seamlessly between windows XP programs and ubuntu. Its very neat. I recommend getting some more RAM though if you decide you like it! ( i got 512 for 20 quid on Ebay and decided it was worth it)

It also allows you to easily reinstall windows when it dies.

Andy

[IMG]http://i50.photobucket.com/albums/f338/andycowman/screen.jpg[/IMG]

---

### Post by twopeak on 2006-04-13
It worked, It seems like grub couldn't find my windows disk, but using a map "command" grub managed to find my windows disk.

---

