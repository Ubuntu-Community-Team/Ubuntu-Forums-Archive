---
title: "Ext4 permissions secure"
date: 2011-10-06
forum: General Help
---

### Post by Moyamo on 2011-10-06
I was wondering how secure ext4 is.

I duel boot Ubuntu and Windows 7 and when I mount the NTFS partition, I have full access to all the files on the drive. 

I know that NTFS (and FATX) don't use permission bits (or at least not the way Linux does).  But I was wondering if it was also possible to bypass Ext4 permission bits. Could someone write a file explorer that ignores permission bits? Or more likely  a mini OS that ignores ext file permissions?

---

### Post by mcduck on 2011-10-06
The permissions of any filesystem are only relevant when running the operating system, they don't protect your files if somebody accesses the drive using another operating system, a live-CD or USB, or removes the hard drive and reads it's contents on another computer.

Physical access to a computer always means full access to the system and all it's files. Which is why protecting your computers from unwanted physical access is an absolute must when it comes to computer security.

The only way to protect your files from unwanted physical access is file (or filesystem) encryption.

(in other words there's no need to write any special file manager application or live-CD, any file manager or live OS will be able to access any unencrypted files from any operating system. The file system permissions are only relevant between *users of a running operating system*).

---

### Post by lcman on 2011-10-06
> **Moyamo said:**
> I was wondering how secure ext4 is.

I duel boot Ubuntu and Windows 7 and when I mount the NTFS partition, I have full access to all the files on the drive. 

I know that NTFS (and FATX) don't use permission bits (or at least not the way Linux does).  But I was wondering if it was also possible to bypass Ext4 permission bits. Could someone write a file explorer that ignores permission bits? Or more likely  a mini OS that ignores ext file permissions?

Boot into windows, download and install truecrypt and encrypt the entire ntfs partition.

---

### Post by Moyamo on 2011-10-07
Thanks for your reply, but my question is not how to secure the NTFS partition (or the Ext4 partition). I know you can encrypt them.

I wanted to know if the Ext4 permissions are as easy to bypass as the NTFS partition.x

---

### Post by blueridgedog on 2011-10-07
> **Moyamo said:**
> I wanted to know if the Ext4 permissions are as easy to bypass as the NTFS partition.x

Yes.  Give me your system and I can access the files regardless of the Ext4 permissions unless they are encrypted.  As stated earlier, physical access means file access as a user can boot on some media that allows them to be "root" and access the files.

In corporate circles this is why physical access is so restricted and why boot media control is essential.

---

### Post by Moyamo on 2011-10-13
Thanks for the answer.

Any files that I don't want anyone to see from now on will be encrypted.

---

