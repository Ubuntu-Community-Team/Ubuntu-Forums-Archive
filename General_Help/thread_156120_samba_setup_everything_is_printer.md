---
title: "samba setup: everything is printer"
date: 2006-04-06
forum: General Help
---

### Post by drpaul on 2006-04-06
I have obviously messed up my samba.conf file because I get the following

paul@paulsbox:~$ smbclient -L paulsbox
Password:
Domain=[MSHOME] OS=[Unix] Server=[Samba 3.0.14a-Ubuntu]

        Sharename       Type      Comment
        ---------       ----      -------
        homes           Printer   Home Directories
        print$          Printer   Printer Drivers
        desktop         Printer
        IPC$            IPC       IPC Service (paulsbox server (Samba, Ubuntu))
        ADMIN$          IPC       IPC Service (paulsbox server (Samba, Ubuntu))
        HL-5140         Printer   HL-5140
Domain=[MSHOME] OS=[Unix] Server=[Samba 3.0.14a-Ubuntu]

        Server               Comment
        ---------            -------
        PAULSBOX             paulsbox server (Samba, Ubuntu)
        TOSHIBA1             portable

        Workgroup            Master
        ---------            -------
        MSHOME               PAULSBOX

Both homes and desktop are listed as type Printer. How do I change them to be Files [or whatever they should be so that I can share files :) 

Thanks for  the help.

Paul

---

### Post by Zimmer on 2006-04-06
First stop is cd to /etc/samba and do a 
testparm smb.conf

See this link for troubleshooting tips
[http://us4.samba.org/samba/docs/man/Samba-HOWTO-Collection/diagnosis.html](http://us4.samba.org/samba/docs/man/Samba-HOWTO-Collection/diagnosis.html)

Have a look here for file sharing tips..
See these links for Info... post #10
[http://ubuntuforums.org/showthread.php?t=108950](http://ubuntuforums.org/showthread.php?t=108950)

This may be useful for you, too
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

---

### Post by drpaul on 2006-04-06
Thanks for the pointers.

For others that shared my problem:  the solution was to remove the "printable = yes" from the [global] parameters section.

Paul

---

