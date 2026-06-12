---
title: "Should I use Samba? (somewhat newbie question)"
date: 2006-05-30
forum: General Help
---

### Post by j1mc on 2006-05-30
Hello, I have a home PC that dual boots Ubuntu and Windows XP on two separate hard drives, and I want to be able to share some files between the two OS's.  I know that I can format a partition on one of my hard drives to the FAT file system, and that both OS's will be able to read/write from this partition, but I'm concerned that this isn't a very secure method of storing files . . . since I'm going to have some personal information in these files, I want to be conscious of security.

I was thinking of setting up Samba on my Ubuntu drive, and having my files accessible from this Samba share.  Does this sound like a good approach?

If so, given that I am not actually trying to network two PC's, but just provide access from two different drives on the same PC will my Samba setup be that much different than if I were networking two PC's?

Finally, will I be able to password protect the Samba share?  Thanks!!

---

### Post by mikeyrb on 2006-05-30
First of all, the only way to securely store files is with encryption.  Passwords on your system will only slow people down, but if they have physical access, they will be able to access your data.  However, physical access won't mean much to an encrypted drive, as you'd have to crack the encryption, rather than just drop a livecd in and copy the files off.

Secondly, you cannot use samba the way you intend to.  Samba will only be running so long as your linux system is booted.  When you boot into windows, you will no longer be running the samba share that you had in linux, rather you'll have your windows file sharing active.  Hence, you will have no sharing between the OS's.

As a solution, you will need to either connect another computer in a network (same lack of physical security), or format a partition using fat or ext2 (you can search the forums for posts about ext2 in windows).  I would recommend just forgetting about the security of the files on your home pc.  Whether you're in linux or windows, the security of the other system is compromised.

---

### Post by Kilz on 2006-05-30
I dont think samba will alow you to share files between hard drives on the same machine. The fat solutution is pretty safe.

---

### Post by j1mc on 2006-05-30
Thanks very much for the informative replies!

---

