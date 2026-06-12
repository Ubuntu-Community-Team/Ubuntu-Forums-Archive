---
title: "chmod/chown:Not effective on Ntfs partition"
date: 2009-12-06
forum: General Help
---

### Post by blurred on 2009-12-06
i hav a ntfs partition which i mounted as /home/user_name/ntfs...
output of user@user:~$ls -l is
> drwxrwx--- 1 root    plugdev    8192 2009-12-07 02:43 Ntfs

my proble is --
1)when i try to give "others" r/w/e privilege by "sudo chmod o+rwx" command
the output of "ls -l" remanins the same.To my commonsense it shud have changed to "drwxrwxrwx".
2)If i try to change the owner to myself using command:"sudo chown user:user /home/user/Ntfs"...nothing happens and root and plugdev remains to be th eowner of ntfs partition..dat is the same output from "ls -s"command...
i am a bit new to linux and very much enthusiastic to learn it...
please show me the correct direction and point out my folly..thnku...

---

### Post by audiomick on 2009-12-06
Hallo.
Don't forget that ntfs is not a Linux file system, but rather a Microsoft system. The chmod command is a linux command, and I am not sure if it works on an ntfs file system.

---

### Post by blurred on 2009-12-06
this means i will never evr b able to share my ntfs content over lan...as "others"dont have any permissions related to any file in my ntfs partition, it is totally inaccessible over lan..the folder do show but cannot be accessed...plz help..

---

### Post by audiomick on 2009-12-06
You should be able to make it accessible as a samba share, or via ssh.

---

### Post by sebastianabate on 2009-12-06
You can set the permissions of the entire partition with the umask option in the mount command. This option set the mask of the permissions that the system sees. If you set the option like 0222, you get 0555 as the partition permissions, if you set the option like 0007, you get 0770, which is the default option (the first number is the sticky bit, always set this at 0). The logic of the option is "0777 - MASK = EFECTIVE_PERMISSIONS".

In your case the command is

sudo mount -t ntfs-3g -o umask=0000 /dev/YOUR_DEVICE /home/user/ntfs

this set the permissions as 0777 for all the files and directories in the partition.

Also the permissions of the folder /home/user/ntfs must be set as 777 before executing the mount command whith the command "sudo chmod 777 /home/user/ntfs".

---

