---
title: "What controls /media mounting?"
date: 2010-05-27
forum: General Help
---

### Post by NutMonkey on 2010-05-27
I have an external USB drive that I partitioned in half, with half vfat and half ext4.  /dev/sdb1 mounts like normal, being owned by me.  But /dev/sdb2 mounts owned as root.  What controls the permissions on the USB disk mounts so I can change it to be owned by me?  I saw a post about mountmanager but that pulls in HAL which I'd rather avoid if possible.

---

### Post by lmarmisa on 2010-05-28
The **Places -> Partitions** mount procedure for **ext4** partitions assigns the root as owner.

You can check this typing the command:

> 
**ls -l /media**
If the **ext4** partition has no label defined, then the UUID (a very long string) is used as the directory mounting point. 

Try to define a label and avoid to use the UUID. I recommend to define the label using GParted. Maybe you will need to install this program using Synaptic, because GParted is not included in the standard Ubuntu installation.

So I will suppose now that you have assigned a label "**DATA**" to the ext4 partition. Maybe you will need to restart your system after the assignment of the label.

The partition is mounted selecting **Places -> DATA**. A directory named **/media/DATA** owned by root will be created too.

You can create a directory for your data owned by your user account (change **myuser** with your actual userid) in the DATA partition typing these commands:

> 
[B]sudo mkdir /media/DATA/MyData
sudo chown myuser:myuser /media/DATA/MyData[/B]
That is all. Store all files and directories you want in this directory **/media/DATA/MyData**.

Best regards,

Luis

---

### Post by lmarmisa on 2010-05-28
An easier alternative to **GParted** is to use the command **e2label**:

> 
**sudo e2label /dev/sdb2 DATA**


---

### Post by NutMonkey on 2010-05-28
Thanks.  I was so used to thinking of the USB drive as a vfat drive that I missed the obvious fact that ext4 can have its own permissions..

---

