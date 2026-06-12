---
title: "Automounting other partitions?"
date: 2006-02-08
forum: General Help
---

### Post by Zeroangel on 2006-02-08
Hi again,

My computer is running low on space on the main HD, so I've decided to throw my old mandrake 10.1 /home/username partition on my other HDD into the mix.

I've symlinked it right to my home folder, but have to mount it manually every time I boot the computer. I would like to know if there are any tools that I can get that will auto-mount the other HDD.

I guess I could try writing directly to fstab, but that scares me a bit as I don't really know the exact syntax and flags to properly mount the drive.

Does anyone know of any method in Breezy that I can use to auto-mount the drive? I might be able to just copy/paste/edit the fstab entry on the mandrake drive but as I said before making fstab edits frightens me.

---

### Post by matthewv on 2006-02-08
Any entry in fstab will be automatically mounted on boot up. If you post the command you use to mount the hdd, I should be able to tell you what to add to /etc/fstab :)

---

### Post by Zeroangel on 2006-02-08
I use:```
sudo mount /dev/hdb6 /mnt/mdkhome
``` to mount.

And I use the following command to symlink:
```
sudo ln -s /mnt/mdkhome/dave /home/dave
rename /home/dave/dave "/home/dave/MDK Home"
```

Also it's an EXT3 partition, but I don't get write access. Would it be wise to chmod it to 777?

---

### Post by matthewv on 2006-02-08
Add this line to your /etc/fstab by running "sudo gedit /etc/fstab"
```

/dev/hdb6       /mnt/mdkhome     ext3    defaults        0       2

```
That should then mount /dev/hdb6 to /mnt/mdkhome, fs type ext3, default options...

The files are probably readonly because they are owned by a different user than yourself, still from your mandrake installation... you should be able to change that with a chown...

---

### Post by Zeroangel on 2006-02-08
It works flawlessly!

Thanks for all your help :)

---

