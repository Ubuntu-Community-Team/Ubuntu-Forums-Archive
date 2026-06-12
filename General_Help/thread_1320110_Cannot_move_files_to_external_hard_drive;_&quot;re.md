---
title: "Cannot move files to external hard drive; &quot;read-only&quot;"
date: 2009-11-08
forum: General Help
---

### Post by tegnoto89 on 2009-11-08
I'm using my buddy's external hard drive to transfer some files so I can do a clean install of karmic, but I'm getting a message that says it's read only.  I tried switching the settings as root to be able to move them, but I get the same error, and some weird things come up in the terminal:

```
tom@tom-laptop:~$ gksudo nautilus

** (nautilus:3967): WARNING **: Unable to add monitor: Operation not supported
e' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory

(nautilus:3967): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:3967): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed


```

Also, when I tried changing the owner and group when changing the permission settings on the hard drive, I got a message saying it couldn't be done because it's a read-only file system.


AND, if I run sudo fdisk -l, here's what I get:

```
sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d6951

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18662   149902483+  83  Linux
/dev/sda2           18663       19457     6385837+   5  Extended
/dev/sda5           18663       19457     6385806   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

```

Is the external hard drive /dev/sdb?  The properties of the hard drive have it listed as having 232GB of space (total used and unused); this has it at 250.

---

### Post by scouser73 on 2009-11-08
You'll need to change the file permissions on the drive firstly.

**1** - Go to **Terminal**, copy & paste this command: **gksudo nautilus** that will open Terminal as root

**2** - Navigate to your new drive, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your drive.

---

### Post by tegnoto89 on 2009-11-09
I'm not trying to be snippy, but that's exactly what I said I did.  I guess I didn't really explain it well- the first terminal output I posted is what I was given while I did that.  I got the same message after setting the permissions to those that you just specified.

---

### Post by michy99 on 2009-11-09
What filesystem is on the external drive? Can you read the files on the drive? Does it work properly on a different system?

---

### Post by ezsit on 2009-11-09
> I'm using my buddy's external hard drive

Did your buddy have any files on the hard drive? Did he partition and format the drive? Has the drive been used successfully on any computer before yours?

Some answers may help.

If there is nothing anyone needs on the hard drive, since fdisk cannot see a valid partition table, nows as good a time as any to repartition and format that drive. Do not do this if someone thinks that drive has any useful data.

---

