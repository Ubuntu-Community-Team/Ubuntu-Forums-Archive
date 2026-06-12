---
title: "USB full install"
date: 2009-12-15
forum: General Help
---

### Post by CaptainMark on 2009-12-15
I was about to try and make a full install onto a usb drive, i need to be able to read the home folder from a windows pc, but obviously windows cant see ext filesysstem, using the live cd installer a partitioned 3gb for the system (ext4 mounted at /) and 5gb for the home folder (fat32 mounted at /home) i got the error message that fat32 partitons shouldnt be mounted in the home folder because it is not designed for this purpose, i could override this or i could make the fat32 partition and add it to fstab mounted in /home later. Is this a serious issue. Will it work okay or has anyone got any suggestions for a different filetype that is linux/windows friendly and can be mounted into /home. Any thoughts?

---

### Post by Groundswell on 2009-12-15
i remember this being talked about a lot when the eee's first came out. people were installing thier os's on flash drives for whatever reason. If you can't find any info here about it, definitely check out eeeuser.com or eeebuntu.org. I can't remember how to do it cause i never needed it :(

it would be somewhere in the archives probably, cause netbook storage has since improved

---

### Post by snowpine on 2009-12-15
If you search the forums, you'll find there are several free utilities for accessing Linux filesystems from Windows. This is a more elegant solution (in my opinion) than forcing Ubuntu to use an inferior filesystem.

If that's not an option for whatever reason, I recommend a separate fat32 data partition for shared data. This partition needs to be the first partition on the drive if you want windows to see it.

---

### Post by CaptainMark on 2009-12-15
yeah sorry, extra software is not an option, have to do it this way somehow. Is it possible to mount the fat32 somewhere else, say /mnt/fat32/ and then symlink the main folders (documents/music/pictures) to /mnt/fat32, 

im not 100% but is it only the fact that, fat32 doesnt support permissions for files (like /home/mark/.dmrc that need specific permissions), that make it unusable for /home

---

