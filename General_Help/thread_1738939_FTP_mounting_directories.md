---
title: "FTP mounting directories"
date: 2011-04-25
forum: General Help
---

### Post by 200k on 2011-04-25
Hello all, I am new to linux and just about have my ftp server up and running but am having trouble mounting external directories.

My home directory is /home/ftp/ and users are locked to the ftp directory.

From within the ftp directory users can access a directory named downloads, so the listing is /home/ftp/downloads/ 

My downloads directory is located on my desktop, and I want to permanently mount the downloads directory @ /home/username/desktop/downloads to /home/ftp/downloads

When I use sudo mount --bind /home/username/desktop/downloads to /home/ftp/downloads the directory binds perfectly, however once I reboot I have to manually re-mount the downloads folder. I have read you can permanently mount directories by editing fstab but I am totally lost.

How should I go about editing fstab? Would mounting external directories like this pose as any security vulnerability when used in conjunction with a ftp server?

Thanks in advance!

---

