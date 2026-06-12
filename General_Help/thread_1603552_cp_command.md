---
title: "cp command"
date: 2010-10-22
forum: General Help
---

### Post by mage200 on 2010-10-22
i want make a bash panel and i want he will copy files from orginal folder to $user folder
i mean
when for explame i type i want install some server he say
cp: cannot stat 'root/Desktop/2/files/beckup/sa-mp-steam': No such file or directory.

any idea?

---

### Post by sikander3786 on 2010-10-22
Are you sure the path actually exists?

cd into the directory and then try cp. Add these lines,

```
cd /root/Desktop/2/files/beckup
```

---

### Post by sgosnell on 2010-10-22
There is usually no Desktop directory in /root.  If you want to copy files to another user, you should start at /home, not /root.

---

### Post by mage200 on 2010-10-23
> **sgosnell said:**
> There is usually no Desktop directory in /root.  If you want to copy files to another user, you should start at /home, not /root.
i mean  panel need root access
when he been installed he install on all the root user
but i only run the panel without install it
and when i try install the samp server this is what he write
"cp: cannot stat 'root/Desktop/2/files/beckup/sa-mp-steam': No such file or directory."

---

### Post by SeijiSensei on 2010-10-23
[QUOTE=mage200;10013861"cp: cannot stat 'root/Desktop/2/files/beckup/sa-mp-steam': No such file or directory."[/QUOTE]

You need a leading slash in the directory path.  "root/Desktop" looks for a directory called "root" and a "Desktop" subdirectory *under the current directory*; "/root/Desktop" looks for the Desktop directory under /root.

---

### Post by mage200 on 2010-10-23
> **SeijiSensei said:**
> You need a leading slash in the directory path.  "root/Desktop" looks for a directory called "root" and a "Desktop" subdirectory *under the current directory*; "/root/Desktop" looks for the Desktop directory under /root.
hmm i just a new in linux
so can you explain me a better please?

---

### Post by sgosnell on 2010-10-23
'root/Desktop/2/files/beckup/sa-mp-steam' starts in whatever directory you are currently in.  You need to add the / before root, using '/root/Desktop/2/files/beckup/sa-mp-steam' to start in the /root directory.  The / makes a huge difference.

---

