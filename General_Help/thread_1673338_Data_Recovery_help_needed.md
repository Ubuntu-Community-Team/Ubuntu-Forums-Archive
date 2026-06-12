---
title: "Data Recovery help needed"
date: 2011-01-22
forum: General Help
---

### Post by uk_dhacker on 2011-01-22
Hi ubuntu users,
My case is a little complicated... I was one of those 'vista sucks i wanna move to ubuntu' user. But before i could install ubuntu my vista crashed. I am a photographer and I maintained all my valuable clicks in vista. 
After the crash, i found out, the hard disk had a few bad sectors too. and the partition on which the important files were there i could not access them using a live usb. 
So i formatted the whole hard disk and installed UBUNTU. All i need now is my photographs and documents from the hard disk.
Can any one suggest me how to do it?? 

Thanks & Regards,
ukdhacker

---

### Post by ronnielsen1 on 2011-01-22
Um you installed Ubuntu to the SAME hard drive that you want to recover from? Bad move. If this is the case I would stop using it immediately. Use a live cd (which won't use your hard disk) and install testdisk to try to recover your files. If this hard drive has bad sectors, it's on its way out and you need a new one

---

### Post by Minn3h on 2011-01-22
When you lose data on a drive it's best to stop writing anything to that drive ASAP to prevent the old data from being overwritten. To that end you may want to check out [http://ubuntu-rescue-remix.org](http://ubuntu-rescue-remix.org), a live disc for recovery that won't write anything to the drive when using it. I believe it includes Photorec which should help you find those missing files.

---

### Post by ronnielsen1 on 2011-01-22
You should have retrieved your files BEFORE doing anything else

---

### Post by ronnielsen1 on 2011-01-22
>  To that end you may want to check out [http://ubuntu-rescue-remix.org]("http://ubuntu-rescue-remix.org/"),  a live disc for recovery that won't write anything to the drive when  using it. I believe it includes Photorec which should help you find  those missing files.

I didn't know about this one. Thanks. Hirens boot cd is good too. I didn't have luck with photorec but it was probably user error. Testdisk worked great for me. 

Do not download this file to the hard drive. Use a flash drive or something

---

### Post by Smart Viking on 2011-01-22
Hey, i hope you didn't format the partitions WITH the pictures right? Cause then it could be.. hard to recover them.

MOST IMPORTAND: Don't use the disk, the more you use it the more you loose.

A nice tool to recover deleted files is photorec.

to install
```
sudo apt-get install testdisk
```

to launch:
```
sudo photorec
```
then follow the instructions.

---

### Post by uk_dhacker on 2011-01-22
I have the live rescue remix now.. what are steps i need to follow to get my data?

---

### Post by uk_dhacker on 2011-01-22
Photorec is working super cool..
but in the rescue remix, i am not able to mount my external hard disk drive. When i plug in the external usb hdd, it says 
" [sdc] Assuming drive cache:write through" 
not sure what that is... 
Also i m not able to locate where it is mounted.

Any help would be greatly appreciated..

---

### Post by ronnielsen1 on 2011-01-22
So this is an external hard drive? Leave it plugged in before you boot up from the live disk

---

