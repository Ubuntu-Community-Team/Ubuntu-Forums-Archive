---
title: "No Root File Defined (Ubuntu 8.10)"
date: 2011-02-07
forum: General Help
---

### Post by carbonway on 2011-02-07
I tried installing Ubuntu on my pc which already has windows XP installed on Drive C. 

My pc configuration :-

P4 2.4 Ghz, 512 MB ram, 80 GB hard disk. The disk has 3 partitions (C=20GB, D=30GB,E=30GB)

 I wanted to install Ubuntu on Drive D as I already have XP installed on C. 

1]  I got to the partitioning menu and opted for manual partitioning. 
2] I deleted D , created a new partition (later tried creating a swap partition which I do not understand why to create) and clicked forward. I got the following message with every try I made.
 
([SIZE=3][COLOR=Red]No rootfile system defined. Please correct this from the partitioning menu[/COLOR][/SIZE]) :confused:
 

 I thought Linux was easy!##% 


I don`t understand the partitioning method on linux a bit. Its very hard to understand unless guided by someone.

---

### Post by CharlesA on 2011-02-07
Hi,

Ubuntu 8.10 has been at End of Life for almost a year now.

Try one of the newer versions of Ubuntu. 10.10 has dead simple partitioning instructions.

---

### Post by mcduck on 2011-02-07
First, you shouldn't be installing 8.10 in the first place. It's an old release, and it's support has already ended. You won't be able to install any software or get any updates for it. Download a copy of the 10.04 LTS or 10.10 instead.

What comes to the eroro message, in addition to creating the required partitions, you also have to tell what partition to sue for what purpose. So you need to set the partition you wish to use as the main pariton to be "/", and the one you wish to sue as swap partiton as "swap".

Anyway, the way partitioning works doesn't depend on the OS, so I assume you either have never done a Windows install, or are actually confused about *drive and partition naming* or the directory structure instead (sda1 or "/" as opposed to c:/ in windows).

The naming is simple, really, sda is the first hard drive, sdb is second hard drive, sdc is third and so on. The number behind that is the number of the partition. So sda1 is the first partition of the first hard drive, and for example sdc2 would be second partition of third hard drive.

"/" or "root" is pretty much the equivalent of the C:/ drive in windows, the main partition of your OS. The difference here is that in Linux & Unix systems other partitions are mounted into directories under that, instead of keeping them completely separate from each other like in Windows.

---

### Post by carbonway on 2011-02-07
> **CharlesA said:**
> Hi,

Try one of the newer versions of Ubuntu. 10.10 has dead simple partitioning instructions.


 I guess you are right. I will get it downloaded today and try it out. 

Do I have to create a Swap partition in it too?.. why is it needed?

---

### Post by CharlesA on 2011-02-07
> **carbonway said:**
> I guess you are right. I will get it downloaded today and try it out. 

Do I have to create a Swap partition in it too?.. why is it needed?

The swap partition is normally created automatically during install, and it's needed if you use hibernate or "suspend to disk"

---

### Post by carbonway on 2011-02-07
> **mcduck said:**
> 

What comes to the eroro message, in addition to creating the required partitions, you also have to tell what partition to sue for what purpose. So you need to set the partition you wish to use as the main pariton to be "/", and the one you wish to sue as swap partiton as "swap".

Anyway, the way partitioning works doesn't depend on the OS, so I assume you either have never done a Windows install, or are actually confused about *drive and partition naming* or the directory structure instead (sda1 or "/" as opposed to c:/ in windows).

The naming is simple, really, sda is the first hard drive, sdb is second hard drive, sdc is third and so on. The number behind that is the number of the partition. So sda1 is the first partition of the first hard drive, and for example sdc2 would be second partition of third hard drive.

"/" or "root" is pretty much the equivalent of the C:/ drive in windows, the main partition of your OS. The difference here is that in Linux & Unix systems other partitions are mounted into directories under that, instead of keeping them completely separate from each other like in Windows.

 You pointed it right- I have been confused about the partitioning directory, as it had numbers from 1 , 5 , 6. there were no 2,3,4(cant explain it all as I don`t remember the names). So it confused me a lot. But I was able to define the D drive based on the size of used space in it as I had emptied D before starting insatllation. There is important data on drive E.

 I will get Ubuntu 10.10 and try installing it. Hope that will be easy. 

 > I figured out that I had given a root or path name (/home) to the one I was installing on and yet i got the root file system error ?? I wonder why.

---

### Post by mcduck on 2011-02-07
> **carbonway said:**
> 
 > I figured out that I had given a root or path name (/home) to the one I was installing on and yet i got the root file system error ?? I wonder why.
the name should be "/", not "/home"

("/"is the root of the file system, "/home" is where user's home directories are located.)

---

