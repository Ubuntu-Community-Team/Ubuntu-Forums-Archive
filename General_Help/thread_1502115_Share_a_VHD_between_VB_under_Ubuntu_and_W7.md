---
title: "Share a VHD between VB under Ubuntu and W7"
date: 2010-06-05
forum: General Help
---

### Post by hariks0 on 2010-06-05
Hi all,

I would like to know if the xp installed in Virtual box of Windows 7 could be used in Ubuntu also. I guess that I will have to create a VHD in the Windows [NTFS] partition to be accessible from both Windows 7 and Ubuntu Lucid and I would have to do the installation of xp under both OS on the same VHD to create/register the VM under both OS.

Are these assumptions correct?

Is it possible to use the same VHD and xp install thereon under both OS?

Or can I just mount the xp install of one OS under the other without installing it again under it?

Thank you in advance.

---

### Post by hariks0 on 2010-06-08
Bump!

---

### Post by hariks0 on 2010-07-08
I have successfully done this. Now I can use the same vhd file for both of the virtual PCs in Ubuntu and Windows 7. Only that I had created the vhd file in NTFS partition so that both Ubuntu and Windows can access it. Installed an OS in Windows Virtual Box and created the same Virtual PC under Ubuntu. Then instead of create a new hard disk, I selected the existin one and everything was OK ! The Virtual PC just booted up like a native install.

:popcorn::p;):D:o:):P

---

