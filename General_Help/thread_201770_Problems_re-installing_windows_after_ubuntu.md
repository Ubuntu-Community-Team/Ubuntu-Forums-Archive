---
title: "Problems re-installing windows after ubuntu"
date: 2006-06-22
forum: General Help
---

### Post by Sonique on 2006-06-22
Hi, I had ubuntu on a pc, but the computer now needs to have windows back on it. What I did was install windows, and deleted all the ubuntu partitions. However when the computer restarted after copying the windows files over to the hard drive, it failed to boot. My computer says its booting from the hard drive, and just freezes like that so it cant find the windows installation.

I don't know if that made sense, but i think its that the master boot record is trying to go to ubuntu even though its not there, how do i make it go to windows? (don't worry guys i still use ubuntu dapper its just i need this computer to go to windows again!)

---

### Post by Sonique on 2006-06-22
Does anyone know? Because if i didnt make it clear, can you just ask what you dont understand because i really need to get windows back on the computer!
Thanks

---

### Post by fer5437 on 2006-06-22
Just try reformat and reinstall your windows since you already delete all the Ubuntu partition.

---

### Post by Sonique on 2006-06-23
[QUOTE=fer5437]Just try reformat and reinstall your windows since you already delete all the Ubuntu partition.[/QUOTE]

Yeah! I had a fat32 partition still on the hard drive i was reluctant to delete, but i backed up the important parts and then deleted, windows is back up fine - we as good as it can get.

Thanks fer5437, thanks a lot!

---

### Post by Apple 101 on 2006-06-23
You could have booted into the Windows Recovery Console and used the mbr and fixboot commands to fix the boot.

---

