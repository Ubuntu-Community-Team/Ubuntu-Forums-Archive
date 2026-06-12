---
title: "Folder gone"
date: 2009-11-22
forum: General Help
---

### Post by venom035 on 2009-11-22
hey


A couple of days ago i created a folder named 2*-11 in ubuntu 9.10 on a separate ntfs partion (D:)

Yesterday i went back to windows 7 and to the ntfs partion (D:), I didn't see the folder that i created under Ubuntu (I know it's a faulty foldername under windows). But when i went back to Ubuntu I couldn't find the folder no more. Can somebody tell me how i can get the folder back?


thx

Just so where clear

First boot Ubuntu 9.10 ext4
Second Windows 7 ntfs
Partion D: nfts

---

### Post by john newbuntu on 2009-11-22
Did you actually use the sudo mount command to mount the ntfs filesystem and then create the folder.
I say this because sometimes we create a directory to act as a mount-point and add files.  But if we fail to mount that mount-point, the files will not reside physically on the destination filesystem.
I also have a feeling that you would have obtained a protocol error when you create a file/folder with asterisk in it.

---

