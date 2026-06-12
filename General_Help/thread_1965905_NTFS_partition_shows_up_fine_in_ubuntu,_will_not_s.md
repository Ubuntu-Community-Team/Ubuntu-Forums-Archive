---
title: "NTFS partition shows up fine in ubuntu, will not show up in windows"
date: 2012-04-26
forum: General Help
---

### Post by olle0047 on 2012-04-26
Sorry if this is the wrong section.

I just installed ubuntu yesterday 11.10. Went over on my windows 7 again to download and burn out 12.04 LTS, however i noticed a drive was missing when i went into win7. It was working just fine before install of ubuntu and it still shows up and is fully useable in ubuntu atm. How can i make it work in windows again? It is by far my most important drive, containing 2TB of things i use every day. Need help ASAP, do not have enough space on my main drive for the files i need in windows right now, hopefully this can be fixed.

BTW in disk manager in windows it shows up as failed. cannot reactivate even if i ask it to.

Thanks
-Ole

---

### Post by duke.tim on 2012-04-26
I took a look at Microsoft's technet and this is what they suggest:

"return disk to online status...if this fails reactivate manually"

[http://technet.microsoft.com/en-us/library/cc787481(v=ws.10).aspx#BKMK_7](http://technet.microsoft.com/en-us/library/cc787481(v=ws.10).aspx#BKMK_7)

[http://technet.microsoft.com/en-us/library/cc786948(v=ws.10).aspx](http://technet.microsoft.com/en-us/library/cc786948(v=ws.10).aspx)

Those should be the relevant links

Also you might want to consider running fsck.ntfs on the disk from ubuntu to check for errors.
If you can reactivate the disk from windows run chkdsk instead of fsck.

---

### Post by olle0047 on 2012-04-26
> **duke.tim said:**
> I took a look at Microsoft's technet and this is what they suggest:

"return disk to online status...if this fails reactivate manually"

[http://technet.microsoft.com/en-us/library/cc787481(v=ws.10).aspx#BKMK_7](http://technet.microsoft.com/en-us/library/cc787481(v=ws.10).aspx#BKMK_7)

[http://technet.microsoft.com/en-us/library/cc786948(v=ws.10).aspx](http://technet.microsoft.com/en-us/library/cc786948(v=ws.10).aspx)

Those should be the relevant links

Also you might want to consider running fsck.ntfs on the disk from ubuntu to check for errors.
If you can reactivate the disk from windows run chkdsk instead of fsck.

Thanks, will try to test it from ubuntu after 12.04 finishes install.
Have tried reactivating both from command line and from disk manager. 
WIll post reply after trying to fix it from Ubuntu!

---

### Post by imachavel on 2012-04-26
unrelated, well I hope it's related:

I don't recommend wubi as I believe they call it. I recommend using a  partition device such as gparted to boot to and then installing OS on  separate partition. If grub stops working well at this point then boot  repair disk can usually fix it. Not sure how wubi works I heard it  installs Ubuntu virtually but I very very much doubt that. Anyway I opt  out of this thread before I encriminate myself by giving bad advice. But  windows fails all the time and installing Ubuntu side by side windows  seems to be the best idea but not through the windows cd ubuntu loading  program once windows has had the boot sector loaded, has booted and  mounted and the OS is running. Always make sensitive changes to a file  system while no OS is mounted: UNMOUNTED = best idea

---

### Post by imachavel on 2012-04-26
you mean using disk part? don't remember how to access it in cmd, diskpart.exe?

then you have list disk list volume list partition and command to activate a partition right? And this isn't working? Re install windows fresh, first, get your files off the disk. And if linux and ntfs(or fat32) don't like each other at boot up in grub, then fix grub with boot repair disk, and if you can get on the linux partition boot repair disk will work from repos without the need to download the .iso and burn it to a disk

---

### Post by olle0047 on 2012-04-26
And BAM! it hit me like a train:
I installed Ubuntu on one half of a dynamic volume that i created in windows. this makes windows all confused when a 100gb is suddenly missing... guess i will have to backup my 2tb somehow and format the drive to be a basic drive again... 

It was all my fault! Thanks for the help folks!

---

