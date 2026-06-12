---
title: "Swap Won't Stay On!!!!"
date: 2009-07-18
forum: General Help
---

### Post by Tman5293 on 2009-07-18
I just noticed today that my swap was turned of so i used gparted to turn it back on. The problem is that now every time I shutdown my computer when I turn it back on my swap is off again.

Can anyone help with this problem???

---

### Post by prshah on 2009-07-18
> **Tman5293 said:**
> I just noticed today that my swap was turned of so i used gparted to turn it back on. The problem is that now every time I shutdown my computer when I turn it back on my swap is off again.


Open a terminal, and give the command```
sudo swapon -a
``` This will automatically permanently activate your swap partition(s)

---

### Post by Tman5293 on 2009-07-18
This command did not work. I got this in return:

swapon: cannot stat /dev/disk/by-uuid/546e20cb-2bf0-410d-88f1-fa60ad45e398: No such file or directory

PLEASE HELP!!!

---

### Post by ptn107 on 2009-07-18
Post the output of:

```
ls -l /dev/disk/by-uuid/
```

---

### Post by Tman5293 on 2009-07-18
This is the output of:
Command:
ls -l /dev/disk/by-uuid
Output:
total 0
lrwxrwxrwx 1 root root 10 2009-07-18 10:13 5060a38d-fb75-47de-9215-331aab0c6881 -> ../../sda5
lrwxrwxrwx 1 root root 10 2009-07-18 10:13 7986aac4-5b67-4138-a405-6370e97e4b35 -> ../../sda1

---

### Post by t4thfavor on 2009-07-18
Your entire swap partition appears to have dissapeared. Maybe youu removed it, or the drive is going bad. I would attempt to recreate it (don't forget to commit the write), and then swapon -a. You may nee to remove the original swap partition, as it will have a new UUID.

---

### Post by SPr on 2009-07-18
```

su
blkid|grep swap

```
should show the UUID and partition of the swap. Compare the result of that with
```

grep swap /etc/fstab

```
The partition ID should match. If they don't then edit /etc/fstab. Always backup any file before editing it.

If you need more help post the results of those two commands here.

---

### Post by Tman5293 on 2009-07-18
The ID's don't match so how do i edit /etc/fstab???

---

### Post by Tman5293 on 2009-07-18
Never mind i figured it out my swap works now.

Thanks for the help!!!

---

### Post by bug67 on 2009-07-18
I like your avatar better'n mine.  I'm jealous!  :P

And now, back to your regularly scheduled program...

---

### Post by Tman5293 on 2009-07-18
Thats cause my avatar is a beast lol

---

