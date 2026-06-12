---
title: "Unionfs image layered over Live USB key"
date: 2010-10-31
forum: General Help
---

### Post by cipherboy_loc on 2010-10-31
Please move this to the proper category, I could not find a more advanced forum off the main page.

After installing Ubuntu to a flash drive, and customizing it heavily, I  am running out of room (8 percent remaining on a 4GB flash drive). While I could go buy another flash drive, I  already have plenty of storage between a 500GB external hard drive and a  DLink NAS. What I would like to do is use unionfs to mount an image (around 6GB in size) over my 4GB flash drive. When it is mounted, all file changes should be synced to the unionfs image, thus "archiving" my flash drive. I have created the 6gb image, formatted it as Ext4 (same type as my flash drive), but when I mount it (using 'unionfs-fuse /media/SG_EHDD/devices/unionfs.dev -o cow /') any changes that I make are not made on the image. I think I am missing an option, namely the -o chroot=SOME_TEXT, but when I put -o chroot=/media/SG_EHDD/devices/, it says it cannot load /media/SG_EHDD/devices//media/SG_EHDD/devices/unionfs.dev. It also gives me the same errors when I cd to /media/SG_EHDD/devices and run unionfs-fuse with ./unionfs.dev for the path to the filesystem image.


Any ideas? I can post more information if needed.

Thanks,
Cipherboy

---

### Post by cipherboy_loc on 2010-11-02
bump

---

