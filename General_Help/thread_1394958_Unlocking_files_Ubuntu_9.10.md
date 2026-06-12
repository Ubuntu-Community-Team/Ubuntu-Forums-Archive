---
title: "Unlocking files Ubuntu 9.10"
date: 2010-01-31
forum: General Help
---

### Post by joelw135 on 2010-01-31
I have three folders on my desktop that I want to delete and they are locked. They have the "X" and "Padlock" symbols. How do I unlock them to delete. They are there from bad installs of the ATI driver.

---

### Post by blueshiftoverwatch on 2010-01-31
Sounds like a permissions problem:

1. Enter **gksudo nautilus** into the terminal
2. Right click on a file/folder -> properties -> permissions
3. Change the owner to your username and select "create and delete files"
4. Change file access to "read and write"
5. Click "apply enclosed permissions to enclosed files"

---

### Post by joelw135 on 2010-01-31
> **blueshiftoverwatch said:**
> Sounds like a permissions problem:

1. Enter **gksudo nautilus** into the terminal
2. Right click on a file/folder -> properties -> permissions
3. Change the owner to your username and select "create and delete files"
4. Change file access to "read and write"
5. Click "apply enclosed permissions to enclosed files"

I tried that and get the error "you are not the owner so you can't change these permissions". 

UDATE: I used the following commands to remove them. sudo rm -r "name of file"

Thanks.

---

### Post by snapback77 on 2010-08-05
Thank you joelw135, this had been trying my patience.  Thank you VERY MUCH!

---

