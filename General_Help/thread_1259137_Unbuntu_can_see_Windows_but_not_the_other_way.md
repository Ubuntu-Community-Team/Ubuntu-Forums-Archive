---
title: "Unbuntu can see Windows but not the other way"
date: 2009-09-06
forum: General Help
---

### Post by mrpbjnance on 2009-09-06
My Unbuntu computer can see and get files from my windows computer
but my windows computer cannot see files or even my unbuntu computer.
Do I have a windows set up problem or Unbuntu set up problem.  What should I look for?

Thanks..  I searched for an answer but not sure if I am using the right search terms

---

### Post by falconindy on 2009-09-06
Have you setup Samba Server on your Ubuntu machine?

---

### Post by coldReactive on 2009-09-06
> **falconindy said:**
> Your Windows partitions are NTFS. Ubuntu can read this. Your Ubuntu partitions are ext3 or ext4. Windows cannot read this.

And if it's ext3 or ext2:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by falconindy on 2009-09-06
> **coldReactive said:**
> And if it's ext3 or ext2:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

Eh, I think I misunderstood the OP, so I corrected myself. If I'm reading it right, he's got two different computers. Not two different OS's on the same box.

---

### Post by mrpbjnance on 2009-09-06
yes I have 2 different computers connected via wireless network.  I have Samba running but not sure if I have it configured correctly.. 

As I said I can see shared folders on my windows computer from my unbuntu computer and can copy files.. but I can't see my unbuntu computer in my network from my windows machine

---

### Post by DeMus on 2009-09-06
> **mrpbjnance said:**
> yes I have 2 different computers connected via wireless network.  I have Samba running but not sure if I have it configured correctly.. 

As I said I can see shared folders on my windows computer from my unbuntu computer and can copy files.. but I can't see my unbuntu computer in my network from my windows machine

This just describes the differences between Windows and Linux:
Windows is open and files can be seen and tempered with
Linux is closed until it is set open by the user.

I know I don't help you with your problem, I just noticed it and had to write this.

---

### Post by snakepit # on 2009-09-06
/etc/samba/smb.conf

---

### Post by coldReactive on 2009-09-06
> **snakepit # said:**
> /etc/samba/smb.conf

And what should it look like if it's configured correctly, and what should the user change if it's not?

---

### Post by 3rdalbum on 2009-09-06
> **snakepit # said:**
> /etc/samba/smb.conf

Or, if you're a mere mortal, try installing the system-config-samba package and configuring Samba that way.

Also note that a personal firewall on the client machine will interfere with the client's ability to automatically detect SMB shares. Turn off the firewall on the Windows machine, or (however one does it in Windows) connect to the Ubuntu machine's IP address rather than its hostname.

---

