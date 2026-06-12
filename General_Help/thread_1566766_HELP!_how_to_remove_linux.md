---
title: "HELP! how to remove linux"
date: 2010-09-02
forum: General Help
---

### Post by geekboy94 on 2010-09-02
Hi, i bought a brand new hard drive and right away installed Ubuntu. I dont know much about computers and my friend gave me the cd. Im using a laptop. So the installation process was easy. Now im trying to remove it so the hard drive can be like the first day i bought it, nothing on it. I was wondering how can i do that by using a cd i can make. almost like making an image to remove ubuntu. Thank you so much.

Also, i dont know what kind of Ubuntu i have so if anyone wants to know please tell me how. thank you and god bless

---

### Post by llawwehttam on 2010-09-02
Simple.

Boot from the ubuntu cd to a live session (running off the disk)

go to System>Administration>Gparted (or partition manager)

delete all the partitions and if you plan on installing windows make a new partition in the space and format it as ntfs.

You can then shutdown and remove the cd.

Before you do this though, can I ask why you want to remove linux?

---

### Post by geekboy94 on 2010-09-02
i dont have the ubuntu cd. so what do i do? and im removing linux because i dont need it. i just want an empty hard drive.

---

### Post by Doomspark on 2010-09-02
I'm an admitted neophyte, but I'd guess you could download a current copy of Ubuntu and make yourself a bootable CD and then proceed as suggested above.

---

### Post by geekboy94 on 2010-09-02
so download ubuntu from the site, put it into the laptop, and then what?

---

### Post by NoNameWill on 2010-09-02
Burn the ISO and use it as a live cd. Then proceed as llawehttam suggests

---

### Post by wojox on 2010-09-02
Use [DBAN]("http://www.dban.org/") 

It will take care of the Mbr as well.

---

