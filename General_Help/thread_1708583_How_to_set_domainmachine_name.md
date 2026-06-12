---
title: "How to set domain/machine name?"
date: 2011-03-16
forum: General Help
---

### Post by rva1945 on 2011-03-16
I have both desktop and notebook with Ubuntu 10.10.

In the desktop, net domain correctly displays domain and server name, but in the notebook both appear as blank. Maybe that's the reason why I can't see the shares in the desktop from the notebook.

How do I set the domain and machine name from the terminal command line?

Thanks

---

### Post by falko on 2011-03-16
```
sudo echo server1.example.com > /etc/hostname
sudo /etc/init.d/hostname restart
```

---

### Post by PunkLV on 2011-03-16
As far as I know there is no such thing as a Workgroup for linux.
I assume you are referring to Samba's workgroup, which purpose is to work with Win machines.
Please post your /etc/hosts /etc/samba/smb.conf and both your PS's IP configuration.

Yeah, forgot about /etc/hostname

---

