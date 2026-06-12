---
title: "Signing the Code of Conduct...Please Help"
date: 2010-03-29
forum: General Help
---

### Post by Jeffster999 on 2010-03-29
I am having 9 kinds of hell signing the COC here is what it is telling me:

gpg: gpg-agent is not available in this session
gpg: can't open `UbuntuCodeofConduct-1.1.txt': No such file or directory
gpg: UbuntuCodeofConduct-1.1.txt: clearsign failed: file open error
jeff@jeff-laptop:~$ gpg --clearsign UbuntuCodeofConduct-1.1.txt


the file is located in the /tmp directory...any assistance would be appreciated

---

### Post by johngreth on 2010-03-29
Try putting UbuntuCodeofConduct-1.1.txt into your home directory.
or
change the directory in the terminal before running the command:
```
cd ~/tmp
```
or
use:
```
gpg --clearsign tmp/UbuntuCodeofConduct-1.1.txt
```

---

### Post by t0p on 2010-03-29
The file is in the /tmp directory; but you are currently working in your home directory.  So, you can move the file to your home directory - by cut-and-paste, or open a terminal (**Applications > Accessories > Terminal**) and typing the command

```
mv /tmp/UbuntuCodeofConduct-1.1.txt ~/
```Or you could change which directory you're currently working in with the command

```
cd /tmp
```Personally, I'd use the first option as I don't like putting stuff in /tmp.  But that's just me - both approaches are perfectly valid.

Oh, I nearly forgot: **Welcome to Ubuntu!!!**

---

