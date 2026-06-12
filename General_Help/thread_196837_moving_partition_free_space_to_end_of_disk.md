---
title: "moving partition free space to end of disk"
date: 2006-06-14
forum: General Help
---

### Post by jlhughes on 2006-06-14
I have a 40GB hard disk divided roughly into 23GB (HDA1) and 17GB (HDA2)

HDA1 is a WidowsXP partition with 15GB free.

HDA2 is a Ubuntu Dapper partition with 3 GB free

I want to reduce the free space in HDA1 to 5GB and add the 10GB to HDA2.

I booted from the live cd and ran GParted. I can reduce HDA1 to any size I want, but I don't see how I can move HDA2 so that it starts at the new end of HDA1.

Is there a way to do this?

Thanks

---

### Post by zxee on 2006-06-14
If i'm following you then you could use the dd comand to do what you want. Make a back up. dd (takes the standard arguments) if=/dev/hdX  of=/dev/hdX in other words "if" is the input you want to move "of" is the output (place) you're moving to.

---

### Post by ????? on 2006-06-14
You can only make ext2/ext3 partitions grow right.. you cannot move it left.. although you can use that space to make a new /home partition

[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

---

