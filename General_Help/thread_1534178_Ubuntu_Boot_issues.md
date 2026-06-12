---
title: "Ubuntu Boot issues"
date: 2010-07-19
forum: General Help
---

### Post by famousforrest on 2010-07-19
I installed ubuntu about a week ago on a 60GB of partitioned hard drive along side windows vista. Since then I've interfaced with both ubuntu and vista several times, and have restarted and shut down my computer several times as well. Over the last few days ive been running exclusively windows but tonight I got the itch to play with ubuntu. when I restarted my computer this time to switch OS, I received the message:

[B]error: no such device: bb30bdea-5ebf-48af-98c4-f0999200687c. 
grub rescue>[/B]

Any ideas to help?

Thanks

---

### Post by lordskid on 2010-07-19
do you see a grub menu before that?

---

### Post by dino99 on 2010-07-19
might be due to bad windoz closing: restart it to close properly

---

### Post by famousforrest on 2010-07-19
Nope no menu came up.
What does "grub" mean?
Also on shutdown I powered off through the start menu, not by pushing the button or unplugging the system.

---

### Post by lordskid on 2010-07-19
grub is a boot loader used by some linux distributions...

anyway what you have is a grub prompt. try the following, but stop if a command fails
```

insmod normal
ls

```
this should list your hard drive and partitions. kindly post it here.

and while you're at it try

```

insmod ext2
set root='(hd0,4)'
linux   /vmlinuz root=/dev/sda4 ro
initrd  /initrd
boot

```

I am assuming your ubuntu is in partion 4 of your hard drive. if you want to make sure after the ls command above there it should list partitions you can check each e.g. ls (hd0,4)/
if ls on one of the partition shows something like /boot take note of this number and substitute the (hd0,N) with the correct one
and change /vmlinuz root=/dev/sdaN

---

### Post by famousforrest on 2010-07-19
typing: 
insmod normal

gives me:
error: no such partition.

Also as per the second bit of code, when I get to the line:

linux   /vmlinuz root=/dev/sda4 ro

I get back:

unknown command 'linux'

---

### Post by famousforrest on 2010-07-19
any other suggestions?

---

