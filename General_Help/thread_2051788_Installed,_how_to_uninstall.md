---
title: "Installed, how to uninstall ?"
date: 2012-09-02
forum: General Help
---

### Post by AlexMcN on 2012-09-02
Hello, 

Here is how i installed linux:

1. Burned the linux ISO.

2. Booted into the cd.

3. I chose to install linux with / along with windows. 

4. Now i want to uninstall as i'm going to fully install it on another computer. 

5. I think its on the same partion as windows as i can see windows docs.


So how can i delete linux ?

Many thanks in advanced.

---

### Post by ajgreeny on 2012-09-02
> **AlexMcN said:**
> Hello, 

Here is how i installed linux:

1. Burned the linux ISO.

2. Booted into the cd.

3. I chose to install linux with / along with windows. 

4. Now i want to uninstall as i'm going to fully install it on another computer. 

5. I think its on the same partion as windows as i can see windows docs.


So how can i delete linux ?

Many thanks in advanced.
Please boot to Ubuntu and run the command ```
sudo fdisk -lu
``` in terminal and post the output back here.  If you have done what you say, you will have to restore the windows bootmanager to the MBR, and how you do that will depend on what windows media (DVD) you have and the version of windows.

Whatever you do, **DON'T** just delete the ubuntu partition or you will be completely stuck without a system you can boot.

---

### Post by AlexMcN on 2012-09-02
> **ajgreeny said:**
> Please boot to Ubuntu and run the command ```
sudo fdisk -lu
``` in terminal and post the output back here.  If you have done what you say, you will have to restore the windows bootmanager to the MBR, and how you do that will depend on what windows media (DVD) you have and the version of windows.

Whatever you do, **DON'T** just delete the ubuntu partition or you will be completely stuck without a system you can boot.

Thanks i will run that code now and post the results :)

I messed around and broke my windows bootleg thing, but fixed it with start up repair, but i still need to delete linux as i need space.

---

### Post by oldos2er on 2012-09-02
> **AlexMcN said:**
> I messed around and broke my windows bootleg thing, but fixed it with start up repair, but i still need to delete linux as i need space.

If you've already restored Windows' boot loader, you can just format any Linux partitions from within Windows (assuming you don't want to save any files on your Linux partitions).

---

