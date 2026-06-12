---
title: "TMPFS questions on Ubuntu 8.10"
date: 2009-10-22
forum: General Help
---

### Post by arisu on 2009-10-22
Hi, I am a newbie using Ubuntu 8.10.

  I recently applied speed tweaks to firefox and vmware workstation by putting firefox profile and vmware workstation .vmem files to tmpfs, respectly.  But I have trouble understanding my ram usage after the tweaks.     

1. How do I check the amount of physical memory each TMPFS is using ?  Further more, is it classified as regular memory or cached memory when I do top or free ?    

2. After the tweak, the swap size increases substantially.  How do I check what is swapped to harddisk ?    

3. What happens if one tries to put stuff to tmpfs beyond tmpfs' size limit ?      

Thanks in advance !

---

### Post by kbielefe on 2009-10-22
I don't know all the answers, but I'll try to help with what I do know.

> 
1. How do I check the amount of physical memory each TMPFS is using ? Further more, is it classified as regular memory or cached memory when I do top or free ? I would use the df -h command.  I believe cached memory on top and free only relates to files you are reading from a disk, so it would be classified as regular memory.

> 2. After the tweak, the swap size increases substantially.  How do I check what is swapped to harddisk ?    That's a pretty deep kernel thing.  I'm aware of no easy way to do it.  It's to be expected, though, if you put a lot of stuff in your tmpfs and don't have a huge amount of RAM.  Basically, the kernel will put the stuff that hasn't changed in a long time into swap so that your faster memory can be used for what you need the most.  You can tweak this a little by "sysctl -w vm.swappiness=10" or whatever number (I think it defaults to 60), but I know of no way to disable swap for certain functions without disabling it altogether.


> 
3. What happens if one tries to put stuff to tmpfs beyond tmpfs' size limit ?      If you set the limit at mount time, it should just give you a disk full message or similar.

---

### Post by dcstar on 2009-10-23
> **arisu said:**
> Hi, I am a newbie using Ubuntu 8.10.

  I recently applied speed tweaks to firefox and vmware workstation by putting firefox profile and vmware workstation .vmem files to tmpfs, respectly.  But I have trouble understanding my ram usage after the tweaks.     

1. How do I check the amount of physical memory each TMPFS is using ?  Further more, is it classified as regular memory or cached memory when I do top or free ?    

2. After the tweak, the swap size increases substantially.  How do I check what is swapped to harddisk ?    


You are probably wasting your time in doing these "speed tweaks".

tmpfs filesystems **steal** RAM from the system, so once you set it aside for tmpfs you no longer have it available for anything else - ever.

Your system - now with less RAM - will now use Swap more because you have just made your system less efficient by reducing its ability to manage the available resources in the best possible way.

VMs use vmem files to have their running RAM stored on a non-volatile medium, when you move these to a volatile medium you make redundant all the reasons that this data is specifically put on something that just won't disappear when the power is off. If you don't need the VM functions that use vmem files, then just turn them off as shown here:

[http://www.fewt.com/2008/06/performance-tuning-vmware-server-on.html](http://www.fewt.com/2008/06/performance-tuning-vmware-server-on.html)

---

### Post by arisu on 2009-10-23
Thanks for the responses.   :) 

To dcstar,

The vmware workstation speed tweak I've followed is exactly the page you provide.  :)

The tweak does not turn off .vmem.  Instead, .vmem is put to /dev/shm via the config options: mainMem.useNamedFile = FALSE and tmpDirectory="/dev/shm".   In my case, I am interested in optimizing virtual machine performance for now.  Hence I am happy as long as ubuntu doesn't swap anything related to virtual machines.

The idea behind both speed tweaks is to lessen I/O workload by putting files which get constantly read from and written to to physical memory. Thus it is best if ubuntu does not swap these files back to harddisk.

===========================

What I've found out so far is the following: 

Below are the result of df -h, top, free -m -t before and after three vmware workstation virtual machines got turned off.  The 3 virtual machine is configured to use 512MB, 512MB, and 768MB of memory. 

Looking at these numbers, I think TMPFS is classified as cached memory in top and free because the cached value drops by ~2200MB, which is roughly the .vmem file size in /dev/shm, while regular memory usage only drops by ~200MB.  Further more, putting .vmem files to TMPFS does not double physical memory usage.  Most of the RES value for vmware-vmx is counted toward cached memory instead of regular memory.  Hence only ~2300MB memory becomes free after shutdown of 3 virtual machines. 

============ 
BEFORE: $df -h 
Filesystem            Size  Used Avail Use% Mounted on
 tmpfs                 7.0G  1.8G  5.3G  26% /dev/shm 

AFTER: $ df -h 
Filesystem            Size  Used Avail Use% Mounted on
 tmpfs                 7.0G  424K  7.0G   1% /dev/shm 

============ 
BEFORE: $top 
top - 18:32:48 up 2 days, 16:28,  9 users,  load average: 0.46, 0.48, 0.58 
Tasks: 169 total,   2 running, 165 sleeping,   0 stopped,   2 zombie
 Cpu(s):  7.2%us, 18.1%sy,  0.0%ni, 69.9%id,  4.4%wa,  0.2%hi,  0.2%si,  0.0%st
 Mem:   8183664k total,  8140692k used,    42972k free,    55752k buffers
 Swap: 12586888k total,   236008k used, 12350880k free,  4217748k cached 

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND             
11628 xxxx      20   0 1197m 834m 793m S   15 10.4  96:59.88 vmware-vmx          
30379 xxxx      20   0  926m 285m 247m S   15  3.6 326:33.32 vmware-vmx                   
26820 xxxx      20   0 1022m 631m 604m S    9  7.9  16:35.36 vmware-vmx          

AFTER: $ top 
top - 18:34:00 up 2 days, 16:29,  9 users,  load average: 0.77, 0.60, 0.62 
Tasks: 166 total,   1 running, 163 sleeping,   0 stopped,   2 zombie 
Cpu(s):  5.8%us,  0.6%sy,  0.0%ni, 93.6%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st 
Mem:   8183664k total,  5753356k used,  2430308k free,    57060k buffers 
Swap: 12586888k total,   232952k used, 12353936k free,  2030052k cached 

============
 BEFORE: $free -m -t
              total       used       free     shared    buffers     cached 
Mem:          7991       7947         44          0         54       4116 
-/+ buffers/cache:       3776       4215 
Swap:        12291        230      12061 
Total:       20283       8177      12105 

AFTER: $ free -m -t
              total       used       free     shared    buffers     cached 
Mem:          7991       5617       2374          0         55       1982 
-/+ buffers/cache:       3579       4412 
Swap:        12291        227      12064 
Total:       20283       5845      14438

---

