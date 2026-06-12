---
title: "The &quot;sudo cp -r&quot; command set the destination folder to only root access?"
date: 2010-02-27
forum: General Help
---

### Post by csh on 2010-02-27
Before, the "sudo cp -r" command automatically set the permissions to make the directory / files can be accessed by others.

But, after I reinstall Ubuntu 9.10 and apply all the latest updates, "sudo cp -r" command set the files to be accessible by root only.

After I copy the codecs directory to /usr/lib by using the above command, not only I cannot view the files inside, SMPlayer and other player software cannot access the directory.

To fix this, I have to run the chmod command to change the permissions.

Does anyone face this problem? Was it caused by the installation of latest updates?

---

### Post by cjhabs on 2010-02-27
The permissions should be picking up your umask.
Enter, in a terminal:
umask

022 is the default - if you have 077 that would cause this problem.
You can set it in .bashrc

---

### Post by csh on 2010-02-27
> **cjhabs said:**
> The permissions should be picking up your umask.
Enter, in a terminal:
umask

022 is the default - if you have 077 that would cause this problem.
You can set it in .bashrc

Thanks for the reply. But, my umask result is 022 not 077.

Any advices?

---

### Post by cjhabs on 2010-02-27
What are the permissions on the source files you are copying?

---

### Post by cjhabs on 2010-02-27
If the permissions are good on the source files, try using the "-p" option with the "cp" command.

---

### Post by csh on 2010-02-28
> **cjhabs said:**
> What are the permissions on the source files you are copying?

I copy from the USB hard disk with NTFS format.

---

### Post by csh on 2010-02-28
I know what are the problems now.

Before I reinstall Ubuntu, I backup some of the files to my USB hard disk with NTFS.

I just realized that if I copy the files to my USB hard disk, the permission will become rwx------ which mean only the owner can has access to it.

Anyway, thanks for your replies.

And, sorry for creating this thread.

---

