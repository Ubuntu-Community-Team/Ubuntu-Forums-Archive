---
title: "Problem with K3B?"
date: 2011-12-09
forum: General Help
---

### Post by Quorlia on 2011-12-09
Hi,

I am finally getting round to upgrading my 9.10 (Netbook remix + KDE) system and stage one is to backup /home.  Since it should fit on a DVD I thought it would be nice and simple just to burn it using K3B.  

When I put a blank DVD (DVD-R) into the drive Ubuntu recognises it and asks what to do but doesn't have any programs it its list.

K3B seems to recognise it and gives me the following information:

Type:	DVD-R Sequential
Media ID:	RITEKF1
Capacity:	510:46:46 min (4.4 GiB)
Rewritable:	no
Appendable:	no
Empty:	yes
Layers:	1
Sessions:	0
Supported writing speeds:	3.0x (4155 KB/s)
4.0x (5540 KB/s)
6.0x (8310 KB/s)
8.0x (11080 KB/s)


However when I go to actually burn my data project it says "Please insert  suitable medium"  I tried a second DVD from the same box and got the same thing.  The drive is a Samsung SE-SO84.

Thanks in advance,

Kirsty

---

### Post by oldos2er on 2011-12-09
Check Settings, Configure K3b, Devices, Modify Permissions, and make sure your user has write permission for your DVD drive.

---

### Post by Quorlia on 2011-12-10
I get as far as "Modify Devices" but there is nothing there about permissions.  K3b calls my drive a writer drive.

Under the system settings K3b::Setup the only thing I can see about permissions is an offer to change them from 660 to 666.

I have 
K3b
Version 1.68.0
Using KDE 4.3.2 (KDE 4.3.2)

I used Nautilus to burn a DVD after I remembered that you could do it that way too so I think this must be something to do with K3b.  Could it just be "fussiness"?  Nautilus reported that there might be a problem with the write after completing it.  There don't seem to be any corrupt files as far as I can tell.....

Thanks for your help.

Kirsty

---

### Post by oldos2er on 2011-12-11
Which version of Ubuntu are you using?

---

### Post by Quorlia on 2011-12-13
9.10.  Please don't tell me to upgrade - backing-up /home to DVD is the FIRST step!!!

---

### Post by oldos2er on 2011-12-13
Your version of K3b is old (as I'm sure you know), and 9.10 is no longer supported. I should've read your first post more closely!

Have you tried any different DVD burning software? Or maybe you have a flash drive you could backup your data to?

---

### Post by oldtimer7777 on 2011-12-13
> **Quorlia said:**
> 9.10.  Please don't tell me to upgrade - backing-up /home to DVD is the FIRST step!!!

Sounds like your system make not be configured to handle the job.

Buy a flash drive or a thumb drive for 10 bucks and migrate your data onto that instead.

If you waited until your system was EOL, to find out your system isn't configured to burn DVD-r??  EOL = S.O.L.

---

### Post by Quorlia on 2011-12-13
I've never had a problem with incremental backups to CDROM using this drive.  It's only now that I've actually had a reason to try and write a DVD.  I'm no longer a heavy computer user so as long as the thing works I prefer to leave it alone - the "if it ain't broke don't fix it" approach.  I now find myself wishing to install some software which is dependant on a newer version so find myself in the uncomfortable situation of having to do a major system upgrade.

I'll find a flash drive and dump it onto that.

Thank you for your time.

Kirsty

---

### Post by oldtimer7777 on 2011-12-13
It isn't your fault that the system is at EOL (End of Life), but that is a reality when using Ubuntu as your primary OS. If you wait until a system is no longer supported to test your DVD burning compatibility, and find that you need to install additional packages to update your system, then you waited too long to test that function. 

But you can still buy a flash drive for 10 bucks from a store, and use that instead. 

Goodluck with that. 

> **Quorlia said:**
> I've never had a problem with incremental backups to CDROM using this drive.  It's only now that I've actually had a reason to try and write a DVD.  I'm no longer a heavy computer user so as long as the thing works I prefer to leave it alone - the "if it ain't broke don't fix it" approach.  I now find myself wishing to install some software which is dependant on a newer version so find myself in the uncomfortable situation of having to do a major system upgrade.

I'll find a flash drive and dump it onto that.

Thank you for your time.

Kirsty

---

### Post by sgtGarcia on 2011-12-13
Are You perfectly sure, that Your home folder is less then 4,4GB, cause "Please insert suitable medium" is shown when capacity of writable medium is too small.
Please check Your home folder with show hidden files/folders ( Ctrl + H ).

---

