---
title: "Copying files with Ubuntu"
date: 2012-04-18
forum: General Help
---

### Post by zebk on 2012-04-18
My Windows PC stopped working for some reason, so I made a Ubuntu disc  and have been running it from that. However I want to reformat my PC and  get Windows back, but when I try to copy things from the "Users" folder  on my hard drive to my external hard drive it says(I'm using the folder  Sample Music as an example): "Error while copying" "There was an error  getting information about the files in the folder "Sample Music" Error  stating file '/media/HP/Users/Public/Music/Sample  Music/AlbumArtSmall.jpg':Input/output error". The external hard drive  works fine and has way more free space then I need to copy this stuff,  but it does this with pretty much everything I try to copy to it.  Copying stuff to the hard drive works fine on my other PC, so it's not  the hard drive, It's Ubuntu. I don't have permission to copy this stuff  or something. When I write click on a folder and go to Properties and  then to Permissions,  if I change the "File Access" thing, it just goes  right back to nothing. How can I copy this stuff? I'm new to Ubuntu so  assume I know nothing about it. Is there some command I can do to  disable the protection or something? I'm not worried about accidentally deleting the OS or anything. I'm trying to copy the Windows "Users" folder to my external hard drive.. Thanks!

---

### Post by for.i.am.root on 2012-04-18
Try using Applications --> Accessories --> Terminal

sudo cp -rfv /media/OLDHDD/Users (OLDHDD is the "name" of your HDD. You have to insert it) /media/EXTERNALHDD/ (EXTERNALHDD is the name of your external. You have to insert it)

If that fails I would bet a bad HDD.

---

### Post by LewisTM on 2012-04-18
You have to be prepared for some problems.
Windows uses the NTFS format for its drives and Linux does not 100% support it, especially if there are some errors on it. You say Windows stopped working? I wouldn't be surprised if some disk corruption damaged your Windows and that same corruption is preventing Ubuntu from properly accessing your files.
To salvage a Windows drive, I find it's best to buy a ATA-to-USB bridge, disconnect the drive and set it up as an external USB drive  on a functioning Windows box. That way Windows can properly fix the errors on the disk and get you back on track. A Windows recovery CD with a disk repair option might also work.

Cheers!

---

### Post by Mark Phelps on 2012-04-18
LewisTM is right -- if Win7 crashed due to filesystem damage, you're not going to be able to work around that using Ubuntu because you're still trying to access a damaged filesystem.

You might have better luck if you narrow down the list of folders you're trying to copy.

In Win7, the convention for storing YOUR stuff is under:

C:\Users\<username>\AppData\  and then, in the subfolders underneath that named Local and Roaming

Maybe if you try to copy the lower-down folders, it will succeed.

---

### Post by zebk on 2012-04-18
Okay thanks guys!

---

### Post by for.i.am.root on 2012-04-19
sudo apt-get -y install ntfs-3g ntfsprogs && sudo ntfsfix /dev/sdaX
sdaX being your hdd (sd = sata, a = first, X = partition number)

This will repair the filesystem allowing you to backup your data using the above command.

Your files should not be under AppData. They would just be in Users/your user.

cp -rfv /media/'hdd'/Users/username /media/external/ will work fine.

---

### Post by forrestcupp on 2012-04-19
> **for.i.am.root said:**
> sudo apt-get -y install ntfs-3g ntfsprogs && sudo ntfsfix /dev/sdaX
sdaX being your hdd (sd = sata, a = first, X = partition number)

That's probably going to be your best bet using Ubuntu. Your problem is definitely with your Windows drive and not with Ubuntu or your external.

You could also try booting to your Windows installation CD/DVD and choose to repair Windows instead of installing it. That might at least get you to the point that you could boot to Windows and copy your files.

---

### Post by for.i.am.root on 2012-04-19
I have had a lot of issues with Windows and copying files that are "damaged" or corrupted. A single corrupted JPEG can cancel an entire copy operation. A real pain if you are copying directories containing tons of files.

I personally use dd to an image file then mount the image and copy the files that way. Prevents further data loss. I have also found that cp deals with corrupted files much better than Windows or nautilus.

The dd method is really only needed when dealing with failed / failing hardware. Something caused Windows to crash which combined with the inability to access data led me to believe the possibility of bad sectors is real. Hence not attempting a repair which could potentially move files to bad sectors.

After recovering your data I would run a non-destructive scan on the hdd. I usually use HDAT for that. Quick and not "very" accurate, however, a good indicator.

Hope I helped.

---

