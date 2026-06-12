---
title: "how to change /home/username/ path"
date: 2011-03-04
forum: General Help
---

### Post by nishizawa23 on 2011-03-04
my disk is full,and i make a new disk which is sda10
and i want to change /home/username path to sad10
so 
1.mount sad10 and format it 
2.copy username to sad10
3.edit /etc/fstab add
/sda10 /home default 0 0
4.restart computer

is this ok?

---

### Post by Red Kelly on 2011-03-04
I'm not 100% certain I know what you wont but I would suggest using the UUID instead of /sda10 because if you ever move the hard drive to a different port it wont know. you can find the UUID by:[COLOR=#000000][FONT=Arial] "sudo blkid" 

Edit: Oh and I think you need to put the file system type after the mount location. Find more by: "man fstab"
[/FONT][/COLOR]

---

### Post by aeiah on 2011-03-04
i cant see that much wrong with what you propose, per se. make sure you consistently refer to the partition as /dev/sda10. even in this post you switched to calling it /dev/sad10 :p

also you should make sure you preserve permissions etc when copying across either using rsync -a or cp -a

as for fstab, just comment out the line that refers to your home directory and create a new one that's the same in all put device name / uuid

see here:
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by nishizawa23 on 2011-03-04
when i mount the /dev/sda10 at /home/Externs
and cp my file to Externs
/dev/sda10 has 30G,but just copy 10G,and said no free space,why?

---

### Post by vanadium on 2011-03-04
Check free space on drives using the command "df". Check file systems used from the command "mount" (I hope your sda10 is not in vfat format).

File systems should be checked when mounted. You disabled checking of the newly mounted partition.

I wonder how you manage to get a partition named sda10. This would normally be a 10th partition on one single drive, sda. For a partition on new drive, I would expect a device designation such as sdb1.

---

