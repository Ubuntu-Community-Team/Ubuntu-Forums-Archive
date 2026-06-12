---
title: "Add folders to Picasa and Google Desktop"
date: 2011-04-20
forum: General Help
---

### Post by webmanoffesto on 2011-04-20
I installed Ubuntu using Wubi Installer. How do I add my D: (data) folder to Picasa and Google Desktop. I see how to add folders in those programs, but I don't see which is my D: drive.

Google Desktop only offers folders under /Home/Tom/ and I don't think D: is under that.

---

### Post by bcbc on 2011-04-20
If you installed Wubi on D:, you'll find your pictures under /host (Places, Computer, File system, host).
If you installed on e.g. C:, then you'll have to mount the D: drive - it will be shown under the Places menu either by the partition label or the size.

If you do have to mount the drive, and want it to be mounted each time you boot, then you need to add it to /etc/fstab. (Note this doesn't apply to the host partition (/host) which is always mounted).

---

### Post by webmanoffesto on 2011-04-23
Wubi is installed on C: 
I want to add a folder on D: 
On my desktop is an icon for "Data" which is D:, and if I right click on it I can unmount it.

But how do I tell GoogleDesktop to search that folder.

[IMG]http://i1232.photobucket.com/albums/ff365/webmanoffesto/GoogleDesktopFolderScreenshotv01.png[/IMG]

I found what I was looking for under "/media/data"
To get there I clicked the "../" in the navigate box twice

---

