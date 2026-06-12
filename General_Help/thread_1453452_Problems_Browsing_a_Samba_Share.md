---
title: "Problems Browsing a Samba Share"
date: 2010-04-13
forum: General Help
---

### Post by pukestain on 2010-04-13
Hello,

I am having some difficulties with Ubuntu 9.10. I have a samba share configured on another Ubuntu 9.08 machine on my network. This shamba share is browsable from all the windows machines on my network. My ubuntu 9.10 machine however cannot browse the share. I can see a folder indicating the workgroup in the Network browser. When I try to open the workgroup folder, I eventually get the notification "Unable to Mount Location. Could not 
retrieve share list from server."

I had previously been running kde(kubuntu) on the 9.10 machine and had no issues in browsing the share.

Anyone have any ideas? 

Many thanks in advance.

---

### Post by mk1w86 on 2010-04-13
I assume the machine you are sharing from is running Ubuntu 9.10, there is no 9.08 release. ;)

Could you please post the output of:

```
smbclient -L [server IP address]
```

from the client machine.

---

### Post by pukestain on 2010-04-13
My bad, the samba share is on ubuntu 9.04


Here's the output from smbclient -L:

Domain=[ADAMS] OS=[Unix] Server=[Samba 3.3.2]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service (funkypuke adams file server)
	share           Disk      File Server share
	print$          Disk      Printer Drivers
Domain=[ADAMS] OS=[Unix] Server=[Samba 3.3.2]

	Server               Comment
	---------            -------
	FUNKYPUKE            funkypuke adams file server

	Workgroup            Master
	---------            -------
	ADAMS                FUNKYPUKE

---

### Post by mk1w86 on 2010-04-13
It looks like your Ubuntu 9.10 client can see the share called share on your server so your problem could be something to do with Gnome, I often have problems mounting samba shares using Nautilus. :roll:

You could try mounting it using the Connect to Server... option under Places.  Choose Windows share from the drop down list, enter your server IP address and any of the other information if necessary. :)

---

### Post by pukestain on 2010-04-13
Thanks. That did solve the problem. 

How can I map that share automatically at startup?

---

### Post by mk1w86 on 2010-04-13
> **pukestain said:**
> How can I map that share automatically at startup?

Have a look under Automagically mount SMB shares (I think it's a typo) here:

[https://help.ubuntu.com/community/SettingUpSamba#Connecting using CIFS](https://help.ubuntu.com/community/SettingUpSamba#Connecting using CIFS)

You will have to create a mount point for the share which you can then bookmark in Nautilus and it will appear under Places. ;)

---

