---
title: "Ubuntu Badger in the office - HELP!"
date: 2006-03-20
forum: General Help
---

### Post by chazaq on 2006-03-20
I enjoyed removing WinXP from one of our crashed desktops and installed Ubuntu Badger.  I about 30 min I had the end-user up on the web and email. SWEEEET!

I really need HELP on printing across my office lan from Ubuntu. 
I can share files from ther server to the Ubuntu box but I cannot print through the same server to a network printer?!?!

I have tried many different combinations of using the Ubuntu Wizard (System>Administration>Printers) No Joy.

While using the printer wizard I can get a drop-down list or servers with printers but I do not get a drop-down list of the printers on the servers.

HELP! I am trying to convert my office over to linux.

(Insane is defined as someone doing the same thing the same way expecting different results... I am going insane):)

---

### Post by gnu2tux on 2006-03-20
Hi,

  Are your printers on a Windows network?

If so, you will need to use samba in order to access the printers.
Install samba first, then let me know how you get on.

Regards,

Al.

---

### Post by chazaq on 2006-03-21
[QUOTE=gnu2tux]Hi,

  Are your printers on a Windows network?

If so, you will need to use samba in order to access the printers.
Install samba first, then let me know how you get on.

Regards,
Al.[/QUOTE]

Yes - I have a Win2K Server as my file/print server.
I can access files on the server from Ubuntu just great so I suspect Samba is working okay.
Thanks for replying... I am anxiuos to get this Ubuntu box to print on our network and then add more Ubuntu machine to our office.  In all I could have 5 or 6 of 12 PCs on Ubuntu by June.  I hope.  
Thanks again Al for responding

---

### Post by Buffalo Soldier on 2006-03-21
A bit long winding... but i hope this helps -> [http://www.networkcomputing.com/showitem.jhtml?docid=1608ws1](http://www.networkcomputing.com/showitem.jhtml?docid=1608ws1)

---

### Post by chazaq on 2006-03-21
**I fixed it!**
Here was the problem...
The machine name (host name) on the Ubuntu box was an old name from when I had Debian Sarge installed before I installed Ubuntu Breezy Badger.  After I corrected the host name **I was able to print !!!**

Thanks y'all
P.S. 
I hope you Aussie's are doing okay down-under. Hurricanes and Cyclones are bad no matter where you live.  
Praying for you.

---

