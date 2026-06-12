---
title: "Permissions on Partitions"
date: 2010-01-02
forum: General Help
---

### Post by carbonbased on 2010-01-02
installed Ubuntu 9.10 tonight. afterwards I formatted another partition to Ext3, only I cannot write to that other partition. and I'm told in a window that my password isn't good for SU permission. I boot up and login automatically as I installed it to do.

How can I now get into admin mode to change permissions for the new partition?

---

### Post by HiImTye on 2010-01-02
```
sudo chown -R <username> <path>
```
path is likely /media/<something>

---

### Post by prshah on 2010-01-02
> **carbonbased said:**
> 
How can I now get into admin mode to change permissions for the new partition?

You can boot using the "Recovery Mode" option from the GRUB (startup) menu. You will be presented with a maintenance menu once the system boots. Open a "Root" terminal (or similar option) and give the command```
passwd yourusername
``` and you will be allowed to directly enter a new password for your username.

Reboot with the command "reboot" and check if you can use sudo; note that automatic login will fail.

---

### Post by carbonbased on 2010-01-02
I went to menus Systems/Administration and used Users Settings. There I chose 'root' and clicked on the "Click to make changes" symbol on the bottom border. Then I established a root account, changed users from the top panel, and made the change to the partition permissions using File Browser by selection the partition's "Propterties/Permissions".

From that panel I gave the Owner to myself, and proper permissions.

Thanks.

---

