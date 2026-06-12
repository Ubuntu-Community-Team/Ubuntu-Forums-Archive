---
title: "Requesting help with vsftpd config and external drive access"
date: 2011-07-29
forum: General Help
---

### Post by TomFumb on 2011-07-29
Any help with my specific situation here would be very much appreciated. I haven't previously been able to find info on this exact problem so sorry if this has been covered before.

I have an external NTFS drive connected to an HTPC running Ubuntu 10.10 and XBMC. I like to FTP to the HTPC to transfer new stuff to the removable drive so I can have it permanently connected.

I have vsftpd running on the machine, and symbolic links (I think - 'ln -s') linking a couple of directories within the removable drive to my ftp user's home directory. As the removable drive is mounted at /media/Iomega\ 1TB/ I have to disable the chroot jail in vsftpd otherwise the FTP user can't reach the sym-linked content. As a result an FTP user can get anywhere in the filesystem.

My router doesn't currently permit external FTP access, but I am thinking about infrequently opening it up to friends, ip-restricted and for short periods of time.

Is there a simple way I can keep the chroot jail AND have my removable drive content available to the FTP users?

I have never really got my head around fstab and the particulars of mounting, so if this is an option some baby-step guidelines would be really helpful.

Many thanks for any suggestions!

---

