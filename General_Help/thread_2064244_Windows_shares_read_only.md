---
title: "Windows shares read only"
date: 2012-09-28
forum: General Help
---

### Post by Beauford on 2012-09-28
Hi,

I am new to Ubuntu, but I think this is more a general Linux issue. I am sharing a couple of Windows folders and can see them no problem in Ubuntu, but it is read only. 

I created the mount point under my user account, but when mounted it says it is owned by root and I only have read access to it.

The following is in my fstab, I tried to give it more permissions, but no luck. How can I get this to be full access for users?

Thanks

//server/share  /home/beauford/Programs cifs credentials=/home/beauford/.smbcredentials,dir_mode=0775 0 0

---

### Post by JKyleOKC on 2012-09-28
Since you're mounting as type cifs, you need to be certain that your /etc/samba/smb.conf file is configured to allow read/write access to the files, and that on the Windows end, file and printer sharing is enabled for those folders/shares.

---

### Post by Beauford on 2012-09-28
> **JKyleOKC said:**
> Since you're mounting as type cifs, you need to be certain that your /etc/samba/smb.conf file is configured to allow read/write access to the files, and that on the Windows end, file and printer sharing is enabled for those folders/shares.
Yes both conditions are true. This appears to be an issue with the folders being owned by root and as such a regular user has no permissions other than read. I can view the files and directories no problem, I just can't create, edit, or delete them.

---

### Post by JKyleOKC on 2012-09-28
You can use additional options in the fstab line to provide full read/write capability, but I'm not certain enough of their exact syntax to advise you about them. Hopefully someone else will chime in with the details.

You might also have a look in the "Tips and Tutorials" forum here, doing a "Search this forum" for "cifs" and see what comes up. I vaguely remember a tutorial a year or so ago on how to make this work, but don't recall the exact title...

---

### Post by Beauford on 2012-09-28
> **JKyleOKC said:**
> You can use additional options in the fstab line to provide full read/write capability, but I'm not certain enough of their exact syntax to advise you about them. Hopefully someone else will chime in with the details.

You might also have a look in the "Tips and Tutorials" forum here, doing a "Search this forum" for "cifs" and see what comes up. I vaguely remember a tutorial a year or so ago on how to make this work, but don't recall the exact title...

Got it to work using some of those options, but not sure it is 100% secure as it involves setting the folders to 0777. I am sure there are other ways - have to keep searching.

---

### Post by oldfred on 2012-09-28
I stopped using Samba as both of my computers are now Ubuntu.

My links are not very up-to-date, but not much has changed. Do not worry about root ownership as NTFS does not support any Linux ownership nor permissions. All you can do is set defaults on the mount.

Howto: Fix Windows share browsing issues 
[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)
Sharing issues
[http://ubuntuforums.org/showthread.php?t=1374369](http://ubuntuforums.org/showthread.php?t=1374369)
See posts by Morbius1
[http://ubuntuforums.org/showthread.php?t=1649380](http://ubuntuforums.org/showthread.php?t=1649380)
[http://ubuntuforums.org/showthread.php?t=1872904](http://ubuntuforums.org/showthread.php?t=1872904)

 HOWTO: Setup Samba peer-to-peer with Windows 
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
For definitive explanation of SMB (CIFS) and how it works, see here .
[http://ubiqx.org/cifs/SMB.html](http://ubiqx.org/cifs/SMB.html)

---

