---
title: "Slow transfer speed with fstab mounted smb share"
date: 2010-05-06
forum: General Help
---

### Post by PlugInPrius on 2010-05-06
I have a smb share setup on a Ubuntu 10.04 32bit computer.

When I transfer a file to the computer with smb://servername/share by going to  places/network my transfer speeds are about 35MB/s. Receiving files is about 35MB/s

When I use fstab to auto mount the share I only get about 12MB/s. Receiving files results in about 35MB/s

This is the line I have in the fstab.
//servername/share /media/media cifs username=myusername,password=mypassword 0 0

I know this is insecure but I just have not got around to doing it the other way with the credential file yet plus this is just for my own internal network.

Why do I get 35MB/s by going to the share via the places/network and only get about 12MB/s when I mount it with fstab?

---

### Post by Jeff Beezy on 2010-06-10
BUMP.  I have this exact problem and always have.  Instead of looking for a solution I just did transfers via FTP since the speeds are much higher

---

### Post by PlugInPrius on 2010-08-16
I'm bumping this up again because I'm still having this issue and have not found a solution yet.

---

### Post by MindGuerrillas on 2011-09-06
I see this exact behaviour too. Does anyone have any advice to offer?

Thanks

---

