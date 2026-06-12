---
title: "rsync (or anyting else) ext3 to ntfs"
date: 2011-02-20
forum: General Help
---

### Post by edpatterson on 2011-02-20
I have searched and read, and read and searched, tested and retested and will be more then happy to appoligize to the other users here if it leads to a working solution.

Source HP Laptop with Ubuntu 10.04
Destination: Vista Home Premium with a 1TB drive formatted NTFS.

UAC is not enabled on the share, in desperation I added the group 'everyone' to the share and security permissions and gave it modify rights.

The mounting via cifs works like a charm. I can manually copy/create/edit/delete files on the share from the laptop day in and out.

I am trying to use rsync to automate the process. There are the usual unable to change time errors and a new mkstemp error. The final error is preventing any files from being copied.

Does anyone know of a way to automatically sync Ubuntu to an NTFS share? I am not married to rsync and would happily replace it if necessary!

Point of the exercise, backup all the machines in the house to this box then back this one box up to an off site server.

Thanks,
Ed

---

### Post by kb2001 on 2011-02-20
I found this, it may help you out

[http://ubuntuforums.org/showthread.php?t=820425](http://ubuntuforums.org/showthread.php?t=820425)

---

### Post by CHRSB on 2011-02-20
Eh, I would look into Remastersys:

[http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)

---

