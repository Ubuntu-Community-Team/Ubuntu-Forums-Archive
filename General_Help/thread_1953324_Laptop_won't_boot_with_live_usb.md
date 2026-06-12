---
title: "Laptop won't boot with live usb"
date: 2012-04-06
forum: General Help
---

### Post by maneesh_ on 2012-04-06
I have a dual boot Win7 and Ubuntu. 
I recently re-installed windows and tried recover grub using this 
[http://askubuntu.com/questions/83771/recovering-grub-after-installing-windows-7](http://askubuntu.com/questions/83771/recovering-grub-after-installing-windows-7)


After doing 
 [B]for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
[/B]
Yeah there were so many easier ways to do this and I have no idea why I chose this. :mad:
I was unable to complete the procedure as I had to do a hard shutdown but I was able to recover the grub. 
There is also an issue with audio card because of which I get a lot of 
  
hda-intel spurious response messages 

which eventually filled up my disk and at this point, i tried to completely format my disk in hopes of fixing it. :confused:
  
Now, when I try to use a liveusb it gets stuck. It does not even enter the single user mode. 
  
I saw some error messages where /proc and /sys were reported as busy. 
  
I am able to get to the shell using gparted. 
  
I have no clue what to do. :mad: 
  
If anyone has any suggestions, please help.

---

### Post by maneesh_ on 2012-04-06
Sos

---

