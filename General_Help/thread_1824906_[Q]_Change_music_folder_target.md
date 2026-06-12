---
title: "[Q] Change music folder target"
date: 2011-08-14
forum: General Help
---

### Post by diospada11 on 2011-08-14
Hello everyone! I'm pretty new to ubuntu and linux. actually, i had only been less than 24 hours since i started using ubuntu 11.04. i have been using Windows since '98 but right now, all i can say is that i'm pretty much impressed with Ubuntu! btw, i'm dual booting Windows 7 and Ubuntu.

with windows, it's easy to have a separate partition (D:) wherein i can store all my valuable files (installers, videos, music, documents, images). after that, i can easily change the target of the default media folders to my folders in drive D. btw, my D partition has NTFS file system.

so here's my question, how can i do the same with ubuntu? i tried searching and all that i found is that i should convert my partition to ext4 so that i can have my Home in a separate partition. this would be very troublesome since formatting would delete all my files and i have no external hard drive to backup all of my precious files. ALSO.. formatting to ext4 would make it unavailable to windows.

any help would be highly appreciated! THANKS!

EDIT: also.. does the filesystem (NTFS or ext4) of the partition, wherein my media files are located, affect the read/write speed in ubuntu in the said partition?

---

### Post by mendhak on 2011-08-14
I've got a similar setup, a C:, a D: (music, pictures) and the Ubuntu partitions.  The only times you'll need to specify its location is when you point your music playing software to a location.  After that, for me at least, I haven't had to refer to it a lot.  Or did you have other scenarios in mind? If you really want, you could try to set up a symbolic link

Navigate to /home/diospada11/, then

ln -s /media/DDrive/Music  Music2

Note: I called it Music2 because you should test it out first and see if it works.  If the symbolic link is created then you could delete the Music folder from home and create a symbolic link for Music.

---

### Post by diospada11 on 2011-08-15
THANKS for the reply! anyways.. i did that symbolic link and it works good. but.. is it normal that my files appear 10 seconds late?

---

### Post by mendhak on 2011-08-15
Do you have a lot of files?  Is the "D Drive" already mounted when you try to access it?  

If you create another symbolic link to a test folder on the D Drive, does that also show up 10 seconds late?

---

