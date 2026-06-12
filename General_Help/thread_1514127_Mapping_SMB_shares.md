---
title: "Mapping SMB shares"
date: 2010-06-20
forum: General Help
---

### Post by prju68 on 2010-06-20
Hi,

I have a NAS (SLUG - NSLU2 Unslung) sharing a folder that is available to all on the network with out password.

smbclient shows it like this:

>     Sharename       Type      Comment
    ---------       ----      -------
    ADMIN 2         Disk      
    DISK 2          Disk      For everyone
    IPC$            IPC       IPC Service ()
    ADMIN$          IPC       IPC Service ()

    Server               Comment
    ---------            -------
    LKGAAC688            

    Workgroup            Master
    ---------            -------
    SPRINGFIELD          LKGAAC688
    WORKGROUP            BTHUB

So I would like to be able to mount this share so that programs on my desktop can access it.

So I have tried this:

> sudo mount -t cifs //lkgaac688/disk\0402 /media/nas -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777and ubuntu helpfully says this:

> mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)Well the device is there smbclient thinks so,  the manual page is about as helpful as a chocolate teapot.

I thought maybe I should replace the server with its IP address... same result.

Taking advice from elsewhere I have swapped my space in the share with \040 as you can see.

So calling all those intelligent Ubuntu gurus out there what stupid thing am I doing wrong?

Thanks
Peter

---

### Post by prju68 on 2010-06-27
Ok so I have figured out what the problem is. The \040 to represent a space in the share name does not work as advertised.

I have created a share without a space.  Now the problem is that I cannot figure out how to rename the share. So does anyone know what should be used to represent a space. 

I realize now having looked for help on these forums before that I probably not going to be successful. Still feel like I should ask and give Ubuntu a chance. My hopes are not high however....

---

