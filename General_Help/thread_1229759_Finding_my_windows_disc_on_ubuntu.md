---
title: "Finding my windows disc on ubuntu"
date: 2009-08-02
forum: General Help
---

### Post by pLind on 2009-08-02
Hi all, im new hear and new to Ubuntu.

Yesterday my computer crashed.. and on the harddrive i had important files that i need for a summer course. So I installed Ubuntu on my other harddrive.

So how do i make Ubuntu find my other harddrive? 

Im sorry if this question has been asked 100 times before but i cant find a newbie answer to this :(

Ps. the windows harddrive wont boot at all, and it makes a clicking noise when it comes to the "hp" menu where u can choose to enter boot menu etc (computer freezes when that harddrive is connected) so I connected it after booting Ubuntu.

Greets - Patrik

---

### Post by merlinus on 2009-08-02
Try testdisk.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by oldos2er on 2009-08-02
Open a terminal (Applications, Accessories, Terminal), and please post the output from this command:
```
sudo fdisk -l
```

---

### Post by pLind on 2009-08-02
> **oldos2er said:**
> Open a terminal (Applications, Accessories, Terminal), and please post the output from this command:
```
sudo fdisk -l
```

Got this back (soz for the swedish) :P

Disk /dev/sda: 200,0 GB, 200049647616 byte
255 huvuden, 63 sektorer/spår, 24321 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Diskidentifierare: 0xa6acd84f

    Enhet Start     Början        Slut     Block    Id  System
/dev/sda1   *           1       23330   187398193+  83  Linux
/dev/sda2           23331       24321     7960207+   5  Utökad
/dev/sda5           23331       24321     7960176   82  Linux växling / Solaris

The disc im looking for is 750 gb


@merlinus

I installed it through package handler synaptic but cant find it in my system? :S

---

### Post by merlinus on 2009-08-02
It is a terminal program.

```
testdisk
```I suggested it because I did not think fdisk would find the hdd, given the errors you were encountering.  There is detailed info on how to use it and screenshots at the link I provided.

---

