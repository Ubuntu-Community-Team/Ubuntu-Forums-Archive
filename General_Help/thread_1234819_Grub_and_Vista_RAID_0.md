---
title: "Grub and Vista RAID 0"
date: 2009-08-08
forum: General Help
---

### Post by ruddyrum on 2009-08-08
Hi,

I have vista x64 installed on two HDD's as a RAID0. I have installed Ubuntu 8.10 on a spare HDD, but when i boot, Grub only gives me the option of booting Ubuntu (and memtest)

I know i will have to beef up my menu.lst but what do i add for a RAID0 config?

Vista x64 is installed on sda & sdc

Any help/info is much appreciated!

---

### Post by ruddyrum on 2009-08-08
I have added the following to the menu.lst without any luck
```
title        Windows Vista x64
root        (hd0,0)
makeactive
chainloader    +1
```Do i have to add anything special as it is booting from a RAID?

---

### Post by ruddyrum on 2009-08-08
Took all afternoon, but its Fixed! :D yay!!

---

### Post by FearMeansControl on 2009-08-15
> **ruddyrum said:**
> Took all afternoon, but its Fixed! :D yay!!

any chance that you'd be able to post the resolution for others to see? ;)

---

### Post by ruddyrum on 2009-08-16
one of the two drives in the raid is bootable... as i am no expert, it was just trial and error as to see which one was the one it booted from!

so basically change the hd0,0 etc in the menu.lst until it boots!

---

### Post by FearMeansControl on 2009-08-16
> **ruddyrum said:**
> one of the two drives in the raid is bootable... as i am no expert, it was just trial and error as to see which one was the one it booted from!

so basically change the hd0,0 etc in the menu.lst until it boots!

thanks... turns out i was having the same problem as you

---

