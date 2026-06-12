---
title: "FreeNAS file permissions...."
date: 2010-01-17
forum: General Help
---

### Post by jbirtsr on 2010-01-17
I have been learning Ubuntu for about 2 months.  I have Ubuntu installed on my HP notebook and all is working Great....!!  I have a FreeNAS server online that I have been using for about 9 months with no problem.  I have Ubuntu 9.10 mounting the FreeNAS share using cifs.  My problem is file permissions.  If i copy a file to my directory on the FreeNAS server, I lose ownership to it, and can open it but I cannot make any changes.  If I drag the file back to my Ubuntu notebook, I have ownership and full permissions and can make any change that I want.  If I create a new file on the Ubuntu notebook and save it on the FreeNAS server, I end up with the same problem, I can not make changes to it.  If I open that same file on the FreeNAS server with my windows XP computer, I can make any change I want and I can save the changes.

When I go look at the file from Ubuntu, I see the changes, but I cannot make changes to it from the Ubuntu notebook.  Any help or ideas would be greatly appreciated....

Thanks in advance,,
Jerry

---

### Post by john newbuntu on 2010-01-18
Does your version of freenas comes with a quixsplore in webgui where you can set permissions.  You could check and see if you can set the umask for different mounts.

---

### Post by jbirtsr on 2010-01-18
The version does have QuiXplorer 2.3 and I have looked at file permissions on the files and folders.  On the top level folder the permissions are drwxrwxrwx.  When I create a new files in windows and save it on the FreeNAS server, the file permissions are -rwxre-rw- and when I save a file from Ubuntu on the freeNAS server the permissions are -rw-r--r--

I might be able to change permissions within QuiXplorer, but I am not sure how to do it.....

but what I am looking for is a way to change the top level folder so I have full access to everything from my Ubuntu notebook....

Thanks,
Jerry

---

### Post by john newbuntu on 2010-01-18
If you open your cifs/samba option in freenas and choose services:CIFS shares-edit, there is an "inherit permissions" option that you could check.  You will have to restart freenas and see if it helps.  (at least with the new files that are copied in and out of the file server)

---

### Post by jbirtsr on 2010-01-18
I just checked my CIFS settings in FreeNAS, and I have the "Enable permission inheritance" box checked.  Not sure if I set that when I installed FreeNAS or if it was checked by default.

---

### Post by SteveHillier on 2010-07-01
Hi guys,
Don't know if you got this sorted but I have a few snippets that might help.

I have a similar problem in using Samba to create and copy files to a FreeNAS server.  I am working with a Windows 7 client but I don't think that makes any difference.

If you configure your FreeNAS CIFS/SMB to use 'anonymous' login I have found (certainly from Windows clients) that files are allocated to FreeNAS UID 21.  We can verify this using our FTP client.

Our problem has manifest itself when we are trying to back up the FreeNAS data to an online backup client.  These clients simply do not like handling UID 21 files.  

However these backup clients are happy to back up any file / directory on FreeNAS where the UID is greater than 1000 (first configured users gets UID 1001).

To get round this issue I have configured CIFS/SMB to use 'local user' access.  I have set up users on FreeNAS to be those running on the Windows Clients.   If you have Windows clients without passwords then check the FreeNAS configuration box to allow users with null passwords.  FreeNAS authenicates the Windows user to the same FreeNAS user and I assume this would be the same in Ubuntu.

I now have the problem of retro fitting all the files created with UID 21 to a UID in the appropriate range.  This is where I was looking to use QuiXplorer, as to date logging on to FreeNAS via SSH and trying to use chown is getting me knowhere.

If any of you guys have an answer on that last bit I would be interested.

Thanks
Steve

---

