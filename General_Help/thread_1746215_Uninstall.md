---
title: "Uninstall"
date: 2011-05-01
forum: General Help
---

### Post by good_times on 2011-05-01
Hi all,
 
Sorry if this has been covered but I couldn't find anything to help in my searches! 
 
I have a dual boot system with Win7 and 10.10 NBR. My wife likes Win7 on the Netbook and I am now getting my own system leaving the netbook in her capable hands. 
 
I want to be able to departition and remove Ubuntu from the netbook and turn the space over to Win7 for her. Don't worry, MY laptop will be Ubunutu all the way!!!!!
 
Can someone please go thorough with me how to do this safely - I'm a little bit scared to try in case I mess the whole thing up!!!
 
Many thanks in advance

---

### Post by ajgreeny on 2011-05-01
First thing to do is restore the win7 boot-loader files and how you do that will depend on what you have available from the netbook maker to restore the system.  I have not used win7 at all, so will have to leave that to others.

Once you have the windows MBR back again you can delete the ubuntu and swap partitions using the windows disk management utility, and either add the space to the windows partition or leave it as a seperate storage partition.

---

### Post by VanR on 2011-05-01
I have done this from Windows 7 using a program called EasyBCD. So download Easy BCD. It's free just google it.
Open EasyBCD 

1. Click on Bootloader Setup
2. Choose your  Windows partition and click on Write MBR.
3. From Windows 7 Disc Management Delete the Ubuntu Partition
4. From Windows 7 Disc Management Extend the Windows partition to take up the now unallocated Ubuntu partition.
Reboot.

Anyway this has worked for me, but do it at your own risk!!
Windows may now run chdisk.

---

