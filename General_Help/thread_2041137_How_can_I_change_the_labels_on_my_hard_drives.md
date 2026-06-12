---
title: "How can I change the labels on my hard drives?"
date: 2012-08-11
forum: General Help
---

### Post by sofasurfer on 2012-08-11
When I use "gparted" it gets confusing as to which drive is which. Once, long ago, I learned how to change the name that would appear for my drives. Now I do not remember how I did it. Do you know?

---

### Post by drs305 on 2012-08-11
You can do it from gparted. Highlight the partition by clicking on it's graphic or in the lower panel, then Partition, Label.

If you aren't using Gparted, from the terminal (sda1 example):
```
sudo tune2fs -L *labelname* /dev/sda1
```

---

### Post by sofasurfer on 2012-08-11
O duh! My problem was that I needed to run gparted from cd, not from terminal.
Then however, as I was starting the cd I got this message... 

busybox
/bin/ash; can't access tty; jpb control turned off
/newroot#

Whats this? never seen it before. I do have a new MB installed, maybe this is a BIOS setting I need to change?

---

### Post by sofasurfer on 2012-08-11
My copy of gparted was real old so I just burned 13.1-2. It worked fine but "exit" did not work...gulp!!! So I held the power off button to shut down. My label change was in effect as seen in terminal gparted. So, I guess I do not have to worry too much about the exit function not working properly? Is there a reason is does not work?
Thanks.

---

### Post by Cheesemill on 2012-08-12
I use the e2label command.

To list the current label:
```
sudo e2label /dev/sda1
```To change the label:
```
sudo e2label /dev/sda1 newlabel
```

---

### Post by oldfred on 2012-08-12
I have used gparted & e2label. 

But I normally use gparted when creating partitions and add labels, but when I forget I usually use Disk Utility to add a label.

---

