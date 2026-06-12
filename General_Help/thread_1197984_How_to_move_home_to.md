---
title: "How to move /home to /"
date: 2009-06-26
forum: General Help
---

### Post by asusx on 2009-06-26
Hey guys,
I have a separate partition for my home directory in ubuntu 9.04, but I'd like to move it to my root filesystem. Is there a way I can do this?

Thanks

---

### Post by geirha on 2009-06-26
1. Run (in a terminal) ```
df -h / /home
``` It will show that / and /home are on separate partitions. This is just for later comparison.

2. Use mount-binding to mount / on a second location (without /home). 
```

sudo mount -o bind / /mnt
df -h / /mnt /mnt/home  # Should show the same information for / and /mnt/home
ls /mnt/home            # Should be empty

```

3. Copy /home to /mnt/home
```
sudo cp -a /home/* /mnt/home/
```

4. Edit fstab, find the line that mounts /home and comment it out (put a # at the start of the line)
```

export EDITOR=gedit # Or whatever editor you prefer
sudoedit /etc/fstab

```

5. Reboot and confirm that /home is now part of / ```
df -h / /home
```

6. The partition that used to contain /home should now be safe to wipe.

---

### Post by aadhar on 2009-06-26
df -h / /home

---

### Post by asusx on 2009-06-26
Thanks!
Worked perfectly

---

