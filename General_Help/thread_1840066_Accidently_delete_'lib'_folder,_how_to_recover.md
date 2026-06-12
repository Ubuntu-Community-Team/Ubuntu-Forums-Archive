---
title: "Accidently delete '/lib' folder, how to recover?"
date: 2011-09-06
forum: General Help
---

### Post by davyasdf on 2011-09-06
Do I have to re-install everything?

It is Ubuntu 10.04

---

### Post by Slim Odds on 2011-09-06
> **davyasdf said:**
> Do I have to re-install everything?

It is Ubuntu 10.04

Yes...

---

### Post by raja.genupula on 2011-09-06
may be sounds bit stupid but give a try , if  you have a back up then you can copy all those things to that location by making a dir at that location .

---

### Post by drs305 on 2011-09-06
Did you delete it via the command line or from a file browser? Depending on how you deleted it (file browser as root), you could look in /root/.local/share/Trash/files to see if the folder is there. If the OS isn't working, you could inspect that folder by mounting the Ubuntu partition from the LiveCD.

If it's really critical, you could try to restore the folder (using the LiveCD if necessary) and an app called TestDisk. It's in the repositories but you'll have to install it (testdisk). It will probably take longer to recover it (if possible) than to reinstall, but if you have critical files you need to recover it might work.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Current_partition_table_status]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Current_partition_table_status")

[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_ext2]("http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_ext2")
(Remember that in Linux a folder is just another 'file')

---

### Post by davyasdf on 2011-09-07
Thanks everyone, I believe my co-worker delete it from command line.

It is not very crucial because it is a test server, we are going to re-install it.

Thanks again

---

