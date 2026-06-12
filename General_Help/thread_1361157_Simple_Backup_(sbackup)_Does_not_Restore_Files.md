---
title: "Simple Backup (sbackup) Does not Restore Files"
date: 2009-12-21
forum: General Help
---

### Post by lakelovers on 2009-12-21
The other day I did a 8.04, fresh install after a disaster trying to get 9.10 working. My files are backed up on an external drive using Simple Backup. My last full backup was when I was on 9.04. I've tried restoring files on the re-installed 8.04. When opening files I've restored, I get the error: "Failed to execute child process "selected app" No such file or directory." I this case I was restoring "Turboprint." Permissions are set for root or my log-in. What should I do to get files to restore?

---

### Post by StuartN on 2009-12-21
> **lakelovers said:**
> What should I do to get files to restore?

Are the versions of sbackup the same in both versions of operating system? packages.ubuntu.com says it is sbackup 0.10.5 in Intrepid, Jaunty and Karmic, so that should not be the issue.

Is there a bug like your symptoms at [https://launchpad.net/ubuntu/+source/sbackup/+bugs](https://launchpad.net/ubuntu/+source/sbackup/+bugs) (There is something similar if the package "menu" is not installed).

Can you read the files within the backup directory and restore them manually?

---

### Post by lakelovers on 2009-12-21
Yes, one event is described in the bug report: the exection window is blank, no restoration info. However, in the bug report, the effected files were restored. I didn't see a solution but then I'm not familiar with the bug reports. I can read the folders but not the files. I have to set permissions and haven't done that in ages so I have a little research to do.

---

### Post by StuartN on 2009-12-22
> **lakelovers said:**
> Yes, one event is described in the bug report: the exection window is blank, no restoration info. However, in the bug report, the effected files were restored. I didn't see a solution but then I'm not familiar with the bug reports. I can read the folders but not the files. I have to set permissions and haven't done that in ages so I have a little research to do.

I meant to include this bug report [https://bugs.launchpad.net/debian/+source/sbackup/+bug/260203](https://bugs.launchpad.net/debian/+source/sbackup/+bug/260203) in my post, which has the error message "Failed to execute child process "su-to-root" (No such file or directory)" due to an installed dependency on the package menu. Is "selected app" the exact text for the child process name in your error message? If you are lucky, then it is simply a missing dependency and installing the missing package will restore full functionality.

When you say you can read folders, but not files, do you mean that the files are not present, or do you mean that permissions prevent reading? If it is a permissions problem and you simply require access to some files, then you could make a duplicate of the entire backup and take ownership of the duplicate. For instance the following will copy all the files (assuming you have space) and change the ownership of the copy.

```
sudo cp -R /pathtoBackup /pathtoCopyOfBackup
sudo chown -R you:you /pathtoCopyOfBackup
```

(where you:you is replaced by your username). Obviously you can also copy and take ownership of the copy of any folder in the backup to save space or if there is something specific you want to extract.

I would not alter the permissions or contents of the original backup, certainly not until I was sure everything had been retrieved.

---

### Post by lakelovers on 2009-12-22
Here is the error message I get. The paticular app is the last notion, of course.

"Details: Failed to execute child process "/home/jerry/bin/ie6" (No such file or directory)"

How will I determine the missing package?

> If you are lucky, then it is simply a missing dependency and installing the missing package will restore full functionality. 

I suppose if I re-installed SBackup I'd lose everthing, so I won't do that.So, if it's a matter of a missing dependency how do I fix it? BTW, images do restore. I'm afraid I'm too much of a dunderhead to move forward with more detail instruction. Thanks for help.

Edit: I forgot to say, I'll be away from the computer until after Christmas. I'll probably be back on the 26th or 27th.

---

### Post by lakelovers on 2009-12-28
I'm still looking for a solution to restoring files. SBackup doesn't restore files that are listed.

---

