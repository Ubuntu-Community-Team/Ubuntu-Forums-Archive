---
title: "0 Byte Files, Rsync, NTFS and db:encryptable"
date: 2009-08-19
forum: General Help
---

### Post by kendoori on 2009-08-19
I am using 9.04 as my day to day OS and maintain a dual boot setup with XP (just in case). I have my working files on an NTFS partition which I've permanently mounted in 9.04. I also run VirtualBox inside of 9.04 regularly. Recently I've run into a condition where I'm somehow creating 0 byte files on the NTFS file. I haven't completely narrowed this down, but they all seemed to be named Thumbs.db:encryptable. These files are not deletable in XP, but I can delete them in Ubuntu. They seem to be sporadically sprinkled on my NTFS drive.

I noticed an odd side effect of this when using an rsync routine that I run on schedule at night which backs up newly written NTFS data to another machine I have that is running 8.10. Even though there are some of these 0 byte files in the source (9.04), somehow thousands of these 0 byte files are spawned on the receiving end of the rsync operation. All these files are hidden, and in addition to the Thumbs.db:encryptable I discovered other hidden files that have patterns like these:  .smores.png.zZzymq (all O byte)

I suspect that this is SAMBA configuration related, and also having to do with permissions etc...

This is an odd one... any help would be appreciated.

---

### Post by The Cog on 2009-08-19
I believe that Windows creates Thumbs.db files whenever it discovers a directory with image files in it. Thumbs.db is the file that contains the thumbnail preview images the windows file explorer shows you. Windows file explorer hides the file itself so that Windows users don't even know it's there.

I have never seen the :encryptable tail-end to the filename though, so I don't know what that's all about.

---

