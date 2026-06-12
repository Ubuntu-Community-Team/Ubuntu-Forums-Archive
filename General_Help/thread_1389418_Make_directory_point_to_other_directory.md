---
title: "Make directory point to other directory"
date: 2010-01-24
forum: General Help
---

### Post by Krudtugle on 2010-01-24
I have tried to find an answer to my question in the forum, but can't really find any spot on information.

I have a partition for all my data (mounted on /mnt/data) and I want to point my /home/<username>/Pictures folder to /mnt/data/Pictures. I.e. I want to point a folder to another folder.

This isn't possible with fstab as I've understood, since that's about mounting volumes. I guess the mount command can be used, but I'd like to mount the directory permanently and I'm not aware of if that's possible with the mount command.

Maybe a soft link can be a solution, but that doesn't feel like a "clean" solution. Then I have to enter the /home/<username>/Pictures directory and then click the soft link?

Any ideas would be great!

---

### Post by mcduck on 2010-01-24
Just delete the existing Pictures directory and create a symlink in it's place (of course make sure to copy all files from ~/Pictures to somewhere else first...)

```
cp -R ~/Pictures/* /mnt/data/Pictures
rm ~/Pictures
ln -s /mnt/data/Pictures ~/Pictures
```

---

### Post by adam814 on 2010-01-24
You wouldn't have to enter it and click anything necessarily.  What you need is a symbolic link.  Do this:

Move anything in your Pictures folder to /mnt/data/Pictures just to be safe:
```
sudo mv ~/Pictures/* /mnt/data/Pictures/
```Then remove your now empty Pictures directory:
```
rmdir ~Pictures
```Now make your symlink:
```
sudo ln -s /mnt/data/Pictures /home/<user>/Pictures
```where <user> is your username.

Now you need to take ownership of the folder.  How you do this will depend on what access you want others to have to your Pictures folder.  I'd suggest this:
```
sudo chown -R <user>:<user> /mnt/data/Pictures && chmod 755 /mnt/data/Pictures
```With that anyone on the system can browse the pictures, but only you can write to the folder.  Of course you can adjust those permissions to suit your needs.

---

### Post by Krudtugle on 2010-01-25
Thanks for the fast replies!

---

### Post by Krudtugle on 2010-01-25
> **adam814 said:**
> 
Now you need to take ownership of the folder.  How you do this will depend on what access you want others to have to your Pictures folder.  I'd suggest this:
```
sudo chown -R <user>:<user> /mnt/data/Pictures && chmod 755 /mnt/data/Pictures
```With that anyone on the system can browse the pictures, but only you can write to the folder.  Of course you can adjust those permissions to suit your needs.

BTW, /mnt/data is a FAT32 partition and I don't think chmod and chown will have any effect there, or?

---

### Post by adam814 on 2010-01-25
Yeah, if it's FAT32 (or NTFS for that matter) disregard that last part.  The rest should still work though.

---

