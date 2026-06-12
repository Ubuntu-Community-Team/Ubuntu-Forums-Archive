---
title: "Added /usr/share partition won't boot properly after"
date: 2010-02-21
forum: General Help
---

### Post by jpaulb on 2010-02-21
My /usr partition was full so I used gparted to make another partition out of some of the /spare space on the HDD. 
Process is quite simple make a new partition, mount it as something, move the contents of /usr/share to the new partition, unmount the partition.
to save time I Wrote the new  entry into /etc/fstab, where the /spare was before. 

mount /usr/share worked quite well until I rebooted, then the system didn't work like it use to. I checked /etc/fstab no mistakes there. ls /usr/share drew a blank, it did not exist; however mount /usr/share worked.

I did not realize that the mounting order in fstab was critical. On boot up /usr/share was being mounted before /usr, which does not work. Changing the fstab from this 

/dev/hda11      /usr/share      ext3    defaults        0       2
/dev/hda6       /tmp            ext3    defaults        0       2
/dev/hda7       /usr            ext3    defaults        0       2
/dev/hda10      /usr/local      ext3    defaults        0       2
/dev/hda12      /spare          ext3    defaults        0       2
/dev/hda8       /var            ext3    defaults        0       2

to this

/dev/hda12      /spare          ext3    defaults        0       2
/dev/hda6       /tmp            ext3    defaults        0       2
/dev/hda7       /usr            ext3    defaults        0       2
/dev/hda10      /usr/local      ext3    defaults        0       2
/dev/hda11      /usr/share      ext3    defaults        0       2
/dev/hda8       /var            ext3    defaults        0       2

work as it should.

I guess everyone but me knew this already

---

### Post by Tourdog on 2010-02-21
jpaulb,

You have just helped me in a very big way .....................  thank you!  I needed that info because before I was ....  :confused: ....  and now I am  ... :) ... !

The Ubuntu Community is a wonderful resource ...........  especially for those of us still running on 7 cylinders...  or 5 cylinders ...  or 3 cylinders !!!

---

