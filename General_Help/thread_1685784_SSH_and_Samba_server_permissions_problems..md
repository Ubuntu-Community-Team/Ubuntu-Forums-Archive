---
title: "SSH and Samba server permissions problems."
date: 2011-02-11
forum: General Help
---

### Post by MMegaTron on 2011-02-11
Hi Guys,

I'm currently doing IT Support for a small company in my home town.  We've got  permissions issues with the linux server which is basically a desktop computer with Ubuntu installed (not Ubuntu server).  The issue we've got  is this; there are two people who log in via SSH using WinSCP from  home.  They sign into the server using user accounts held on it.  Samba  is installed for all of the Windows XP machines to connect locally,  mounting the drive using 'Map Network Drive'.  This means that all  machines connecting locally are accessing the server via the Samba  interface using the 'share' user login.  

Because Linux is very strict with permissions, when one user who works from home tries to connect via SSH and creates files or folders on the drive, nobody else can  modify those files (they don't have permission because shes the owner!).  She also has issues when trying to modify files  created in the office when accessing them from home - she cant put files in certain folders.  I have tried getting her to login via the  'share' user, which wouldn't log in (presumably something to do with  Samba permissions) as I thought this would be the easiest way to solve  the problem.  I have tried changing the the permissions of WinSCP  directly, and I have also tried setting all users to a group with read  and write permissions - but there seems to be no way to do this  permanently - every time a new file is created it defaults back to read  only access and the permissions need to be changed manually.  I have  also tried to login from home using Putty, which supposedly would let me  mount the share folder in Windows remotely using 'Map Network Drive'.  No success.  This problem is also causing issues with the backup which  is unable to backup some of the files - including when using the sudo  (root privelidges) command, which makes it serious.

I was  wondering if anyone can you think of any  solutions to this problem?  Any help would be greatly appreciated!

Thanks

Jack

---

