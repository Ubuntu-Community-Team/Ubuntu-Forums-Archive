---
title: "install ubuntu in a drive"
date: 2011-04-22
forum: General Help
---

### Post by athalsten on 2011-04-22
hi, i am new in ubuntu. i cant install ubuntu in a specified space. i have a 500 gb hard disk . it is impossible  to me backup the files bcz they r 400 gb. and i create a 20gb space in my hdd. i use windows xp also. so when boot i try along with another OS. then manually select partition. i formated it ext4. but when i click next. then it says root not selected or some thing about the root ( i forgotten) . 


Plz any one help me to setup the ubuntu in the 20 gb partition.


i am using win xp SP 3

trying to setup ubuntu 10.10

---

### Post by Hedgehog1 on 2011-04-23
During the manual install, you will also need to identify that partition with a '/' (said  'root') mount point.

[IMG]http://img19.imageshack.us/img19/9673/05allocdrivespace3.png[/IMG]:

Also, be sure to install the boot loader on the drive itself:

[IMG]http://img855.imageshack.us/img855/7153/09installbegin.png[/IMG]


***The Hedge***

:KS

---

### Post by athalsten on 2011-04-23
thanks for reply just put /

nothing else?

and may i need a swap area? if yes what is the size?

---

### Post by RJ12 on 2011-04-23
> **athalsten said:**
> thanks for reply just put /

nothing else?

and may i need a swap area? if yes what is the size?

Most people say Swap should be at least the size of your RAM, sometimes a little more.

---

### Post by athalsten on 2011-04-23
what happen if i dont creat aswap space. my ram is 2gb and 2gb is a great use to me. my hdd almost full:(

---

