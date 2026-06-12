---
title: "bad nightmare about grub crash ?"
date: 2009-12-26
forum: General Help
---

### Post by dinw3 on 2009-12-26
Hi , i have problem with my ubuntu 9.10 kernal , doesnt boot .it just show black or blank screen 

more details :

i get this when the pc start , it is " Gurb 2 menu " 

[php]GNU GRUB version 1.97 beta 4
ubutntu , linux 2.6.31-16-generic
ubutntu , linux 2.6.31-16-generic (recovery mode )
ubutntu , linux 2.6.31-14-generic
ubutntu , linux 2.6.31-16-generic (recovery mode )
memory test (memtest86+)
memory test (memtest86+ , serial console 115200)[/php]
then i tried to figure out my way , so i follow this link

" reinstall grub 2 " 
[https://help.ubuntu.com/community/Grub2#Editing%20Menus%20During%20Boot](https://help.ubuntu.com/community/Grub2#Editing%20Menus%20During%20Boot)

which is the easiest way i found , acatually the things didnt go smothly , so i had one problem regarding 


[COLOR=DarkRed]#sudo mount /dev/sda1 /mnt[/COLOR]

i got this mount:wrong fs type bad option bad superblock on /dev/sda1

the answer is : do that by 
#sudo fsck /dev/sda1 

the link : [http://ubuntuforums.org/showthread.php?t=1357690&highlight=mount%3Awrong+fs+type+bad+option+superblock+%2Fdev%2Fsda1](http://ubuntuforums.org/showthread.php?t=1357690&highlight=mount%3Awrong+fs+type+bad+option+superblock+%2Fdev%2Fsda1)

finally my problem and my nightmare is terminated and thanks for john and others tutorials in this community

best regards  , this my all steps that i followed to solve problem

---

### Post by dinw3 on 2009-12-26
I try to switch it on again , then i press c , it drop me to command line 


GMU GRUB version 1.97''beta4

( Minimal BASH-like line editing is supported. For the first word, TAB lists
possible command completions. Anywhere else TAB lists possible
device/file completions. )

sh:grub> 

what should i do ?

---

### Post by dinw3 on 2009-12-26
:( can someone give me a hint or suggestion ?

---

### Post by dinw3 on 2009-12-27
any link or hint to follow

---

### Post by john newbuntu on 2009-12-27
Look at:
[https://help.ubuntu.com/community/Grub2#Editing%20Menus%20During%20Boot](https://help.ubuntu.com/community/Grub2#Editing%20Menus%20During%20Boot)
and search for the string "Using CLI to Boot"

---

### Post by dinw3 on 2009-12-27
thanks john i will read that

---

### Post by dinw3 on 2009-12-27
hi john , again it seem all the alternative options difficult to follow so i try to follow the this method 
**SIMPLEST - Copy GRUB 2 Files from the LiveCD**

#sudo fdisk -l

then i notice that my system is on /dev/sda1   *  linux 


[COLOR=DarkRed]#sudo mount /dev/sda1 /mnt[/COLOR]

i got this mount:wrong fs type bad option bad superblock on /dev/sda1

---

### Post by john newbuntu on 2009-12-27
Run a filesystem check from liveCD using the command:
sudo e2fsck -C0 -p -f -v /dev/sda1

---

### Post by dinw3 on 2009-12-27
:P hi john the nightmare is gone

---

