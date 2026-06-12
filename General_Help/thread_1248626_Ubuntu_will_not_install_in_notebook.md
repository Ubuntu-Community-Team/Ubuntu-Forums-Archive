---
title: "Ubuntu will not install in notebook"
date: 2009-08-24
forum: General Help
---

### Post by mightyh on 2009-08-24
I have installed Ubuntu 9.04 in my PC successfully but when I tried to install it in my laptop, it will not complete the installation due to "Invalid Argument." I tried another Ubuntu installation CD but always come up with the same pop up warning immediately after the files are copied to my hard drive. I am trying to install it within the Windows so I can have a dual boot. I can operate it as a live CD and it works fine but I don't want to use the Install Option while running it because I might erase my Windows OS. I am still trying to learn more about  Linux and that is the reason for the dual boot. Need some help on this matter because I am really beginning to like Ubuntu. Thanks.

---

### Post by Bucky Ball on 2009-08-24
Is one of them a 64bit and one of them not? You don't install within Windows for a dual-boot. You put Ubuntu on a separate partition and choose which OS you want from a menu which Ubuntu will set up as part of its install (it will detect your Windows install).

There are a LOT of tutorials and HOWTOS about this out there. One of the better ones is here:

[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")

If you manual partition, there is no risk of erasing your Windows. It is on an NTFS partition. Linux uses EXT3 by default and you will see your Windows install plainly there when you get to that part of the install. Just don't touch it. Simple. But choose 'Manual Partitioning', NOT anything else that allows Ubuntu to 'automagically' partition your hard drive for you!

You will need to make the partitions:

/
/home
/swap

... at least but they are there in drop down menus, you just need to choose them. That link will tell you all ... :)

Good luck and welcome to Ubuntu and the forums.

---

