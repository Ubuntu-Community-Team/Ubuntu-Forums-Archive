---
title: "boot problem"
date: 2012-04-28
forum: General Help
---

### Post by retired1 on 2012-04-28
Dual boot 12.04 & xp, fresh install - when I try to boot into xp from initial boot screen, after 2 seconds instead of starting xp i get the initial boot screen. When I installed 12.04 I chose xp as place to put mbr.

---

### Post by oldfred on 2012-04-28
Welcome to the forums.

Did you not install the grub2 boot loader to the MBR? Windows boots from MBR to PBR or partition boot sector and Windows has to have its boot code in the PBR not grub. 

Post the link to Bootinfo to confirm what is where. Boot-Repair cannot fix the exact problem you have if you installed grub to the Windows PBR. But will let us see what is where so we can suggest the best solution.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or Create BootInfo report & post the link to a run of boot info script so we can see your exact configuration.

If you want to know how Windows boots, article has lots of detail, but just reviewing pictures explains it.
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by schowalla55 on 2012-04-28
Having boot issue also,
updated from update manager to 12.04, at bios it installed a dual boot, I have xp on another hard drive. If I try to start from original drive, says no partion found, on any recovery, but in my windows hard drive I can get to recovery, and at recovery it goes no further than command prompt. Will let me log on. 
Thanks


I found another post that said, all updates should be installed first.
could that be my issue?
Thanks again

---

### Post by retired1 on 2012-04-28
Oldfred - thanks for your reply - it was faster for me to reinstall lubuntu rather than download the cd. When I installed 12.04 I was given the choice of installing the mbr to sda1 Windows or the hard drive. Typically I install the mbr to the window partition but that didn't work this time so I reinstalled and put the mbr on the hard drive. So now all is fine - thank you.

---

### Post by oldfred on 2012-04-28
Sometimes reinstall is faster if you have no important data to save. Glad you got it working.

---

