---
title: "Printing using lp or lpr"
date: 2011-03-15
forum: General Help
---

### Post by dazman19 on 2011-03-15
Hi

I have a label printer connected to a windows machine and its shared. and other windows machines can print to this label printer. but i need to be able to print to it from the linux box using lp or lpr.

I have been following this article on how to get he labels printing, but I am unable to have any luck whatsoever.

Here is where i am at:

bennett@ezyvet:~$ smbclient -L AECRECEPTION -U administrator
Enter administrator's password:
Domain=[VSG] OS=[Windows 7 Professional 7600] Server=[Windows 7 Professional 6.1]

        Sharename       Type      Comment
        ---------       ----      -------
        ADMIN$          Disk      Remote Admin
        AECLABEL        Printer   AECLABEL
        C$              Disk      Default share
        IPC$            IPC       Remote IPC
        print$          Disk      Printer Drivers
        Users           Disk
        vsgconversion   Disk
Domain=[VSG] OS=[Windows 7 Professional 7600] Server=[Windows 7 Professional 6.1]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------


I also have done this:

bennett@ezyvet:~$ sudo lpadmin -p AECLABEL -h 192.168.58.116 -i smb://AECRECEPTION/AECLABEL -P /home/bennett/drivers/zebra2844/zebra4.ppd
lpadmin: Unable to connect to server: Connection refused

The firewall on the windows machine has turned off.

I can see 2 printers, cups cant find any more printers. It just says its searching for eternity. I believe the only reason why the 2 printers show up in cups is because they are network printers?

Can anyone help i have been googling for hours.

Cheers
Daryl

---

### Post by bk60544 on 2011-03-15
I used "windows printer using SAMBA".  Instead of using "browse", enter the IP address of the Windows machine it is connected to, and then the "share name" of the printer.  The result will look something like this: 192.168.1.12/Labels6.

---

### Post by dazman19 on 2011-03-15
nah still no go.

I have spent nearly the entire day fluffing around with this thing.

I am still getting 
Tree Connect Failed NT_STATUS_ACCESS_DENIED

It says its printed but it has not.

---

