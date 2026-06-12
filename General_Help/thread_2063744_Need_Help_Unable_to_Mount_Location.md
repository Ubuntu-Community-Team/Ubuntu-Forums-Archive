---
title: "Need Help Unable to Mount Location"
date: 2012-09-27
forum: General Help
---

### Post by HereForLeUbunt on 2012-09-27
So first off, i am not able to start Windows and am using a DVD copy of Ubuntu to start up. Im pretty sure that if i reinstall windows that i will be able to start up with windows again but by doing this all my data will be wiped clean and so a friend recommended me to Ubuntu. Whenever i go to the go on the top bar and computer i see my 750 GB Hard Disk: OS but whenever i click it i get this 

```
Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details. 
``` 

and so after googling for a while i found that to fix this you need to do sudo apt-get install ntfsprogs but when i do that i get 

```
 Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ntfsprogs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  ntfs-3g:i386 ntfs-3g

E: Package 'ntfsprogs' has no installation candidate 
```

and so i read on farther and they told me to do this: sudo apt-get update && sudo apt-get install ntfsprogs
BUt whenever i do that i get this 
```
 Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ InRelease
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ InRelease
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise InRelease
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Release
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Release
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Packages/DiffIndex
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Packages/DiffIndex
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Translation-en
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Translation-en
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/main TranslationIndex
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/restricted TranslationIndex
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/main Translation-en_US
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/main Translation-en
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/restricted Translation-en_US
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/restricted Translation-en
Ign http://security.ubuntu.com precise-security InRelease                      
Ign http://archive.ubuntu.com precise InRelease                                
Ign http://archive.ubuntu.com precise-updates InRelease
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]
Hit http://archive.ubuntu.com precise Release.gpg         
Get:2 http://security.ubuntu.com precise-security Release [49.6 kB]
Get:3 http://archive.ubuntu.com precise-updates Release.gpg [198 B]
Hit http://archive.ubuntu.com precise Release                       
Get:4 http://archive.ubuntu.com precise-updates Release [49.6 kB]
Get:5 http://security.ubuntu.com precise-security/main amd64 Packages [169 kB]
Hit http://archive.ubuntu.com precise/main amd64 Packages         
Hit http://archive.ubuntu.com precise/restricted amd64 Packages
Hit http://archive.ubuntu.com precise/main i386 Packages 
Hit http://archive.ubuntu.com precise/restricted i386 Packages
Hit http://archive.ubuntu.com precise/main TranslationIndex
Hit http://archive.ubuntu.com precise/restricted TranslationIndex
Get:6 http://archive.ubuntu.com precise-updates/main amd64 Packages [393 kB]
Get:7 http://security.ubuntu.com precise-security/restricted amd64 Packages [3,969 B]
Get:8 http://security.ubuntu.com precise-security/main i386 Packages [174 kB]  
Get:9 http://security.ubuntu.com precise-security/restricted i386 Packages [3,968 B]
Get:10 http://archive.ubuntu.com precise-updates/restricted amd64 Packages [6,755 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Get:11 http://archive.ubuntu.com precise-updates/main i386 Packages [398 kB]
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Get:12 http://archive.ubuntu.com precise-updates/restricted i386 Packages [6,732 B]
Hit http://archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://archive.ubuntu.com precise/main Translation-en
Hit http://archive.ubuntu.com precise/restricted Translation-en
Hit http://archive.ubuntu.com precise-updates/main Translation-en
Hit http://archive.ubuntu.com precise-updates/restricted Translation-en
Fetched 1,256 kB in 4s (299 kB/s)                 
Reading package lists... Done
W: Duplicate sources.list entry cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)/ precise/main i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04.1%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20120823.1)_dists_precise_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)/ precise/restricted i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04.1%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20120823.1)_dists_precise_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ntfsprogs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  ntfs-3g:i386 ntfs-3g

E: Package 'ntfsprogs' has no installation candidate 
```

So overall, all i want is for me to be able to take things out of my hard drive and put them into a flash drive but everytime i try to open my hard drive unable to mount location and the first code error thing i posted has it in there, its exit code 13.


Thank you for all who take there time to read this and help!

---

