---
title: "Copying files with EFS Encryption"
date: 2009-08-12
forum: General Help
---

### Post by limbick on 2009-08-12
Hi there
 
My work computer recently crashed.  I am able to view the contents of the failed drive in linux, but not in windows.  My company automatically encrypts large amounts of data on our harddrives.
 
Long story short, I can't access the drive in windows to decrypt the files, and I haven't found a way to copy the files in ubuntu (from one NTFS partition to another NTFS partition).  When I attempt to do so, I get a message that access is denied, based on file permissions.
 
Is there a way to copy the files, without worrying about the encryption?  I can unlock the files once they are on the new harddrive, as our encryption keys are stored on the domain.  The problem is just physically moving the data.
 
All help is appreciated!
 
brando

---

### Post by zkriesse on 2009-08-12
check out this [http://technet.microsoft.com/en-us/library/bb457065.aspx](http://technet.microsoft.com/en-us/library/bb457065.aspx)
and this [http://technet.microsoft.com/en-us/library/cc782898(WS.10).aspx](http://technet.microsoft.com/en-us/library/cc782898(WS.10).aspx)

---

### Post by limbick on 2009-08-12
I appreciate the fast response Zachk18, however, both of those links assume that you can get into windows to do what needs to be done.  If I was able to read the drive in windows, I wouldn't have any problems.  Windows says the drive has IO errors, while Ubuntu allows me to browse (and copy non-encrypted files).
 
I am looking for a copy function in Ubuntu that will allow me to copy the EFS encrypted files, so they can be properly accessed on my replacement laptop.  Once they are copied, I will be able to open them.

---

