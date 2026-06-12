---
title: "mount-ownership-rw data partition"
date: 2009-08-27
forum: General Help
---

### Post by texas.chef94 on 2009-08-27
Recently installation of larger HD left me with an empty 160GB external.

I created a single ext3 partition titled data1. Please advise as to creating ownership, mounting and rw

Thanks

---

### Post by scouser73 on 2009-08-27
Please follow the instructions set out in this tutorial for mounting hard drives: [[COLOR="Red"]**Mount External Hard Drives**[/COLOR]]("https://help.ubuntu.com/community/Mount/").

Go to **Terminal**, copy & paste this command: **gksudo nautilus**

That will open Terminal as root, navigate to your new drive, **Right Click**, select the **Permissions** tab change the **Owner** drop-down menu to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write**, **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your drive.

---

### Post by Engenia on 2009-08-30
Didn't quite work as I expected.

I've mounted my 2nd HDD in fstab with ...
"/dev/sdb1 /media/disk auto defaults 0 0"
When I open nautilus as suggested with ...
"gksudo nautilus"
the following is returned..
"Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing."

(I'm thinking that's trying to tell me something! /var/lib/samba contains nothing but "secrets.tdb")

Then Nautilus opens as expected.
Selecting the "Tree" view, in the left hand plane, right clicking "disk" & selecting "Properties", then the "Permissions" tab, reveals the Owner as root.

The problem comes next, when I attempt to select the Owner, as "errol" (me). It reverts almost immediately to "root"

The same thing happens for any directory or file on /media/disk

Where am I going wrong?
Do I need to enable user sharing?

NB: when I quit out of nautilus, the terminal window shows
"--- Hash table keys for warnings below:"
followed by a bunch of file names, many of which are on /media/disk/

---

### Post by texas.chef94 on 2009-08-30
> **Engenia said:**
> Didn't quite work as I expected.

I've mounted my 2nd HDD in fstab with ...
"/dev/sdb1 /media/disk auto defaults 0 0"
When I open nautilus as suggested with ...
"gksudo nautilus"
the following is returned..
"Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing."

(I'm thinking that's trying to tell me something! /var/lib/samba contains nothing but "secrets.tdb")

Then Nautilus opens as expected.
Selecting the "Tree" view, in the left hand plane, right clicking "disk" & selecting "Properties", then the "Permissions" tab, reveals the Owner as root.

The problem comes next, when I attempt to select the Owner, as "errol" (me). It reverts almost immediately to "root"

The same thing happens for any directory or file on /media/disk

Where am I going wrong?
Do I need to enable user sharing?

NB: when I quit out of nautilus, the terminal window shows
"--- Hash table keys for warnings below:"
followed by a bunch of file names, many of which are on /media/disk/

I tried all this within Nautilus as well and based on your mount point
or how you identified this partition you may have to make some changes. However this is what finally worked for me.
sudo mkdir /media/DATA

sudo mount -t ext3 /dev/sda1 /media/DATA

sudo chown allen /media/DATA

Have a great Sunday or is it Monday there already

Allen:lolflag:

---

### Post by Engenia on 2009-08-30
"sudo mount -t ext3 /dev/sdb1 /media/DATA"
didn't work. Couldn't find the ext3 file system .... 'cos I'd formatted it NTFS ](*,)
"sudo mount -t ntfs /dev/sda1 /media/DATA"
worked fine, but
"sudo chown errol /media/DATA"
failed, probably because it's ntfs.
Think this is covered at [http://www.linuxforums.org/forum/debian-linux-help/52000-ntfs-partition-doesnt-accept-chmod-777-a.html](http://www.linuxforums.org/forum/debian-linux-help/52000-ntfs-partition-doesnt-accept-chmod-777-a.html)

Perhaps I'll format it ext3 instead.

---

### Post by texas.chef94 on 2009-08-30
> **Engenia said:**
> "sudo mount -t ext3 /dev/sdb1 /media/DATA"
didn't work. Couldn't find the ext3 file system .... 'cos I'd formatted it NTFS ](*,)
"sudo mount -t ntfs /dev/sda1 /media/DATA"
worked fine, but
"sudo chown errol /media/DATA"
failed, probably because it's ntfs.
Think this is covered at [http://www.linuxforums.org/forum/debian-linux-help/52000-ntfs-partition-doesnt-accept-chmod-777-a.html](http://www.linuxforums.org/forum/debian-linux-help/52000-ntfs-partition-doesnt-accept-chmod-777-a.html)

Perhaps I'll format it ext3 instead.

Sorry about that I assumed you were dealing with Linux all way which would exclude ntfs

---

