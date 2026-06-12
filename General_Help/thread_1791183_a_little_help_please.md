---
title: "a little help please"
date: 2011-06-26
forum: General Help
---

### Post by rbrick49 on 2011-06-26
Hi folks I just want a little bit of help from some of you hard disk gurus.I have windows7 on sda1.I have ubuntu natty on sdb1 I just purchased 2 more sata hard drives I have 2 sata burners how do I get my 2 new hard drives to work I plugged them in but no boot screen I have six sata slots so can someone give me some pointers please its an asus motherboard
regards Ronnie

---

### Post by ronacc on 2011-06-26
try booting the live cd and see how the drive letters are assigned now , installing the new drives may have changed that , also check your bios boot order and make sure it points to the drive that has grub on it as the 1st hard drive .

---

### Post by dino99 on 2011-06-26
fisr things to do:
- read the motherboars doc, specially the sata part
- check that hdds are well configured (master/slave/...)
- then check that all hdds are recognised by bios

---

### Post by rbrick49 on 2011-06-26
ok ronacc and dino will give that a check tomorrow and see what shows up thanks guys 
regards Ronnie
by the way sda and sdb are 2 seperate hard drives as well

---

### Post by sparker256 on 2011-06-26
> **rbrick49 said:**
> Hi folks I just want a little bit of help from some of you hard disk gurus.I have windows7 on sda1.I have ubuntu natty on sdb1 I just purchased 2 more sata hard drives I have 2 sata burners how do I get my 2 new hard drives to work I plugged them in but no boot screen I have six sata slots so can someone give me some pointers please its an asus motherboard
regards Ronnie
On your motherboard your sata connectors are numbered. This is how bios will see then so I would connect your new hard drives to sata 3 & 4 and your two burners to 5 & 6. 

After that go into bios and see if the first four are hard drives with 3 & 4 being your new hard drives and the next two are your burners.

If all that went well boot a live cd/USB and use the disk utility or gpart to make sure Linux is also seeing them. If all well then you can now install Linux on your new drives

Bill

---

### Post by rbrick49 on 2011-06-26
Thanks Bill will check all that tomorrow to late at night now and my eyes arent that bright anymore not saying much for the brain either
regards Ronnie

---

### Post by sparker256 on 2011-06-26
> **rbrick49 said:**
> Thanks Bill will check all that tomorrow to late at night now and my eyes arent that bright anymore not saying much for the brain either
regards Ronnie
One other thing that is important is to install with a separate /root and /home. If you have to reinstall you will be very thankful you took the time to make your install that way.

Bill

---

### Post by rbrick49 on 2011-06-26
thanks folks all is ok I found a sata cable hooked to non existant floppy drive,this box is a haf box . I had 5 sata cables plugged in when only 2 burners and 2 drives so all is ok
thanks folks regards Ronnie

---

### Post by Perfect Storm on 2011-06-28
Moved to General Help.

---

