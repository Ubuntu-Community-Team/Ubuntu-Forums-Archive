---
title: "can't boot! ubuntu keeps moving hard drive labels!"
date: 2009-11-30
forum: General Help
---

### Post by maxxerific on 2009-11-30
help! 
   every time I add or remove a hard dirve to my tower (which happens often as i have a few drive trays installed with different disks for storage popping in and out on any given day)
Ubuntu renames my filesstem harddrive. 

Originally (druing install) it was sdb1 
added a hd - it became sda1 and then sdc1 

well - now it won't boot at all. i get a waiting for root system error during load (after main grub menu)



"- Boot args (cat /proc/cmdline)
- check rootdelay= (did the system wait long enough?)
- check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! does not exist. Dropping to a shell!"




how do i reset grub, or make the fileststem HD a constant id? 

i tried 
this advice: 

sudo grub-install --root-directory=/media/ubuntu /dev/sdc 

(where sdc was the roo filesystem at that time - and /media/ubuntu was directory i had created by booting off the live CD...

does anyone know what i'm doing wrong?

---

### Post by eldragon on 2009-11-30
google UUID

---

### Post by jacobs444 on 2009-11-30
you need to mount the main disk by uuid instead of by /dev/sd?

i am supprised it isn;t already doing this.

give this a read

[http://www.linux.com/archive/feature/146951?theme=print](http://www.linux.com/archive/feature/146951?theme=print)

---

### Post by maxxerific on 2009-11-30
thanks guys - will try that right away....

---

### Post by maxxerific on 2009-11-30
okay well - sounded great 
   but i went to edit fstab - and it turns out thr root filesystem was already assigning by UUID
so i guess that's not the issue.
erk

---

### Post by maxxerific on 2009-11-30
well - my instinct is that ubuntu will only finish booting when the filesystem HD is assigned sdb
if i add another hard drive (right now there are two. Or take away the second HD
  grub loads me into a console

---

### Post by maxxerific on 2009-12-04
solved: 
   ended up reinstallng grub2 (twice! don't know why it didnt' work the first time)

now everything seems hunky dory

---

