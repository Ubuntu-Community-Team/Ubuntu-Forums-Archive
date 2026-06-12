---
title: "Problem caused by using ntfs-config"
date: 2009-09-04
forum: General Help
---

### Post by chandru155 on 2009-09-04
My ntfs drives in my computer are WindowsXp,Backup,Fun,Education,Recovery(totally 5 ntfs drives). So I tried to automount these ntfs drives using ntfs-config. 
   At First, i added Fun and Backup ntfs drives to ntfs-config and then restarted my system to check whether they are working or not. They worked when i logon back. (Now Fun and Backup ntfs are added to automount)
 Then,again i added Education,Recovery ntfs drives. Then i gave the option revert to reset the automount, but only the last added drives Education,Recovery ntfs drives were resetted.  Fun and Backup ntfs drives are still auomounting. 

 I checked ls command,
```
chandru@ubuntu:/media$ ls
BackUps   cdrom   Education   Fun   RecoveryDisk
BackUps_  cdrom0  Education_  Fun_  Windows Xp Pro

```So i got two labels(Backup and Backup_). What might be the problem. Also
```
/media/BackUps_/Linux/Download For X
```In the path, "_" is added to my ntfs drive labels. I thing i did some thing wrong in ntfs-config. Help me solve the problem.

Since, the drives are  Fun and Backup drives are automounting, i deleted the entries in FsStable. I saw two things. FsStable and pre-fsstable. Dont know what to do. Help me to solve this problem

 Ntfs-config, is not working now. It shows error,unable to mount the partition

---

