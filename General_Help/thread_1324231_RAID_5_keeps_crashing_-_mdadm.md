---
title: "RAID 5 keeps crashing - mdadm"
date: 2009-11-12
forum: General Help
---

### Post by giovannizero on 2009-11-12
I have three 1.5 TB drives running in a RAID 5 using mdadm and it keeps removing drives as faulty. I've tested the drives and I don't think they're going bad. If I unmount and remove everything I can force the rebuild of the array and it will work fine again for a few days. I'm at a loss as to what's going on. 

I ran [sudo mdadm --run --query --detail /dev/md0 ]("http://pastebin.com/m359fa017"). Which tells me two devices are faulty, but I get different results when I check on each partition individually. 

[LIST]
[*][mdadm -E /dev/sdb1]("http://pastebin.com/m30057667")
[*][mdadm -E /dev/sdc1]("http://pastebin.com/m6136dc49")
[*][mdadm -E /dev/sdd1]("http://pastebin.com/m5ea5cfef")
[/LIST]

I've run two of the drives in a striped array for over a year with no problems and just switched over to a RAID 5 in ubuntu 9.10 using mdadm. I really don't think the drives are going bad. I've rebuilt the array 4 or 5 times now and everytime it works fine for a day or two and then drives start dropping.](*,)

---

### Post by giovannizero on 2009-11-13
I ran tests on both drives that were marked as fail using smartctl doing short and long offline tests. Both drives had no problems so it looks like my drives are good, my RAID keeps on failing.

For those curious, I have two WD drives and one Samsung.

---

### Post by laluz on 2009-11-25
Check this thread of mine. It may help you. [http://ubuntuforums.org/showthread.php?t=1281922](http://ubuntuforums.org/showthread.php?t=1281922)

---

