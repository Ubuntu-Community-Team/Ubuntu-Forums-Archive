---
title: "Testing software raid5"
date: 2011-01-30
forum: General Help
---

### Post by omega21 on 2011-01-30
Hey there,
I have a ubuntu desktop with raid5 on 4 disks. (The system root is on a seperate, unraided drive). I was wanting to test the raid array's ability to recover itself while my data is stored safely on a new external drive. 

What's the best way to do this?
Thanks!

---

### Post by omega21 on 2011-01-30
...anyone?

---

### Post by omega21 on 2011-01-31
anyone at all??

---

### Post by psusi on 2011-01-31
That should be pretty obvious: yank out a drive.

---

### Post by omega21 on 2011-01-31
That's what I was thinking.. but then what?

Should I throw another drive in and try a restore? How to I revert back to the old drive after?

---

### Post by jeebustrain on 2011-02-01
when you pull a drive, it will put the array in a degraded state. Add a new drive (or format the old drive in another machine) and re-add it back to the array. It will rebuild the stripe across the new disk.

---

### Post by psusi on 2011-02-01
If you have a write intent bitmap then the rebuild will go very quickly if the missing drive was not gone long, since it will only rebuild the parts that changed.  Otherwise, it will take a while as it rebuilds the whole thing.

---

