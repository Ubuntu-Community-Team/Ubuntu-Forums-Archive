---
title: "how to install gpart from source"
date: 2009-12-05
forum: General Help
---

### Post by Gemu on 2009-12-05
Greetings! I was wondering if there is something I can do to get gpart to install while running ubuntu 9.04 live cd? I can't seem to get it to install with apt get. I can download the file and try to manually install it but it comes up with an error 2 message and terminates when I do sudo make.

 I accidentally erased my whole 400 gig partition with everything I own on it last night with gparted. I clicked on set disk label hit ok and boom it was gone. I thought I was going to label my backup FAT32 partition. Wrong! 

Thankfully knoppix 5.1 had it already installed on it and to my amazement I (merry christmas to me from whoever invented gpart) was able to recover my partition table and reboot into my system. 


 It bugs me that I couldn't get it to install in Ubuntu live 9.04 . It installs fine on my HD install with apt get.

---

### Post by howefield on 2009-12-05
> **Gemu said:**
> It bugs me that I couldn't get it to install in Ubuntu live 9.04 .

Gparted is already on the live cd. Why would you need to install it ?

---

### Post by akakingess on 2009-12-05
> **Gemu said:**
> Greetings! I was wondering if there is something I can do to get gpart to install while running ubuntu 9.04 live cd? I can't seem to get it to install with apt get. I can download the file and try to manually install it but it comes up with an error 2 message and terminates when I do sudo make.

 I accidentally erased my whole 400 gig partition with everything I own on it last night with gparted. I clicked on set disk label hit ok and boom it was gone. I thought I was going to label my backup FAT32 partition. Wrong! 

Thankfully knoppix 5.1 had it already installed on it and to my amazement I (merry christmas to me from whoever invented gpart) was able to recover my partition table and reboot into my system. 


 It bugs me that I couldn't get it to install in Ubuntu live 9.04 . It installs fine on my HD install with apt get.
I don't know if it is different from the live CD, but "sudo apt-get install gparted" doesn't automatically install it for you?

EDIT:  Sorry, I didn't know it was already on the LiveCD, although I should have... sorry and disregard my message, I guess.

---

### Post by oldos2er on 2009-12-05
Sounds like you need testdisk, not gparted. [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by wojox on 2009-12-05
Click on System > Administration > Partition Editor

---

### Post by Gemu on 2009-12-05
> **howefield said:**
> Gparted is already on the live cd. Why would you need to install it ?

  Its gpart mate. A tad different animal. An extremely useful one if you lose your partition table.

---

### Post by Gemu on 2009-12-05
Here is the actual error message that I got if someone can help me figure this out. I should be able to install it shouldn't I? 


ubuntu@ubuntu:~/Desktop/gpart-0.1h$ sudo make
make -C src
make[1]: Entering directory `/home/ubuntu/Desktop/gpart-0.1h/src'
make[1]: Leaving directory `/home/ubuntu/Desktop/gpart-0.1h/src'
make[1]: Entering directory `/home/ubuntu/Desktop/gpart-0.1h/src'
gcc -Wall -O2 -pedantic -DVERSION=\"0.1h\"   -c -o gpart.o gpart.c
gpart.c:72: warning: built-in function ‘log’ declared as non-function
In file included from /usr/include/fcntl.h:217,
                 from gpart.c:52:
In function ‘open’,
    inlined from ‘main’ at gpart.c:1224:
/usr/include/bits/fcntl2.h:51: error: call to ‘__open_missing_mode’ declared with attribute error: open with O_CREAT in second argument needs 3 arguments
make[1]: *** [gpart.o] Error 1
make[1]: Leaving directory `/home/ubuntu/Desktop/gpart-0.1h/src'
make: *** [gpart] Error 2
ubuntu@ubuntu:~/Desktop/gpart-0.1h$

---

### Post by Gemu on 2010-01-25
No one has any suggestions on this? I can intall it fine on my Hd install but I need to be able to install it on the live cd.

---

