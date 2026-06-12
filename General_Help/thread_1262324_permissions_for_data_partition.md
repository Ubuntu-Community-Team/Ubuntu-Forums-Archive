---
title: "permissions for data partition"
date: 2009-09-09
forum: General Help
---

### Post by stuart.reinke on 2009-09-09
I've created a new ext3 partition which I want to use to store data.

I do not want it to mount automatically (It doesn't)

I do not want it to be linked to my home folder. I want to move stuff there manually.

From Google I've learned that I need to use the chmod command.

Here is where I get confused...

Gparted calls the partition /dev/hda6

It's mounted as /media/disk

Only root has permission to use it, I would like to make is usable for all users.

How do I use the chmod command to change permissions?

Is there a GUI way to do the same thing? (I haven't found one yet)

Thanks for any help.

---

### Post by baseface on 2009-09-09
```
sudo chmod 0666 /whatever/directory
```

---

### Post by stuart.reinke on 2009-09-09
> **baseface said:**
> ```
sudo chmod 0666 /whatever/directory
```

what is the 0666 for?

---

### Post by baseface on 2009-09-09
octal permissions for rw-rw-rw

---

### Post by baseface on 2009-09-09
and read the chmod man page.

---

### Post by stuart.reinke on 2009-09-09
> **baseface said:**
> and read the chmod man page.

I always do. 

I stare at them like a monkey doing a math problem.:confused:

I wish I understood what i was reading.:(

---

