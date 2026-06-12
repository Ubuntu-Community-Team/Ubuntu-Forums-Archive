---
title: "mount.ntfs fill slowly the ram (natty)"
date: 2011-08-02
forum: General Help
---

### Post by winterhold on 2011-08-02
As the title say mount.ntfs slowly fills all the memory from my computer and slows it considerably, I had issues of performance so I checked out what process was taking a lot of resources. It came out to be mount.ntfs that fill the memory up without never releasing it until the ram is full. Then it's impossible to do anything ( big lag ), and then after several minutes it come back when the memory is finally freed. (Example at this moment the command: sudo top, show me for the user:  root, RES: 1.3g,  %CPU: between 0-4, %MEM: 34.6, command: mount.ntfs.)

I have Ubuntu 11.04(natty) and a vm(virtual box) on a drive formatted in ntfs ( to be easily swapped on windows when necessary )

Is there any known issues or possible solution to fix this ? The drive is mounted with the ui (Nautilus 2.32.2.1) and I have 4 gb of ram

any help will be appreciated

Thanks,

---

### Post by winterhold on 2011-08-02
Now the two first process of the command: sudo top when sorted by memory usage are :

 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND               
 3041 root      20   0 1815m 1.8g  652 S    0 45.5   0:42.30 mount.ntfs            
 3102 atvubunt  20   0 2318m 1.6g 1.5g S   16 41.6  27:38.52 VirtualBox   

just insane that mount.ntfs take more than every other program

System Monitor shows  used 3.8gb (97.1%) of 3.9gb

anyways i'll unmount than mount again my drive so the memory get some memory cleaned, because it's getting laggy

---Edit---
I forgot to say that it does the same thing with the swap once the ram is full the swap is getting filled so there is nothing else to do.

I also wrote to the developers of mount.ntfs(ntfs-3g-devel@lists.sf.net) about this issue. Version of mount.ntfs is: ntfs-3g 2010.8.8 February 2010 NTFS-3G( 8 ).

thanks

---

