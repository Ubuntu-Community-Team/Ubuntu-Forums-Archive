---
title: "Accessing Network files"
date: 2009-07-17
forum: General Help
---

### Post by RunningBear on 2009-07-17
I have the Netbook remix installed on a Dell Mini 9 and want to access files on another computer over my network. I can open the remote files from the network icon on the right of the screen but if I want to access a remote file from an application such as open office, the networked share does not show up in the location list of the open dialog.  I have looked in /mnt to see if the remote system is mounted there, but cannot find it.  How do I open a remote file from an application?

Thank You

_DAVID WARNER

---

### Post by litspliff on 2009-07-17
what protocol is the network share? NFS, SMB, FTP, etc.


for you to access it, it must be mounted somewhere on your local file system, so point the program at that location in your filesystem.

i use smb4k for smb, so here is my example.
/home/user/smb4k/server/share/filename

---

### Post by RunningBear on 2009-07-17
The share is on a Windows machine running Windows XP.  I assume it is either NFS or SMB but do not know how to tell which. When I click on the network icon on the right side of the screen in the netbook remix, the shares are accessible and if I click on a remote file, it will open in the appropriate application.  It is when I am in an application and wish to open a remote file that I have difficulty.  I know the share must be mounted somewhere but cannot find it.  Where is a share that is mounted using the facility embodied in that network icon mounted?

Thanks

_DAVID WARNER

---

