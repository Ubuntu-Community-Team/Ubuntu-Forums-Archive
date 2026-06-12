---
title: "Editing sudoers programmatically"
date: 2009-12-11
forum: General Help
---

### Post by guillaumev on 2009-12-11
Hi,

In order to configure automatically client machines through debian packages for this project ([http://wiki.github.com/guillaumev/ecafeserver](http://wiki.github.com/guillaumev/ecafeserver)), I was wondering if there is a way to edit the /etc/sudoers file programmatically. I know that, manually, it's possible to edit that file using visudo, but how can you do it programmatically ? I've tried changing the permissions and then changing them back again, but it actually breaks the sudo program:
```

chmod u+w /etc/sudoers
echo "new line" >> /etc/sudoers
chmod u-w /etc/sudoers

```

After I run this script, I get the following error when I try to run sudo again: /etc/sudoers is mode 0640, should be 0440.

Is there any way to change the /etc/sudoers file programmatically ?

Thank you.

---

### Post by derrick81787 on 2009-12-11
If the package is installed as root (which is usually the case), then you shouldn't have to change the permissions.  Just edit the file as part of the installation.  You'd better do a lot of testing and have a liveCD handy the first few times you try it though.  From what I understand, if you screw up that file, you can't really fix it again without the help of a liveCD or something similar.

---

### Post by sisco311 on 2009-12-11
> **guillaumev said:**
> Hi,

In order to configure automatically client machines through debian packages for this project ([http://wiki.github.com/guillaumev/ecafeserver](http://wiki.github.com/guillaumev/ecafeserver)), I was wondering if there is a way to edit the /etc/sudoers file programmatically. I know that, manually, it's possible to edit that file using visudo, but how can you do it programmatically ? I've tried changing the permissions and then changing them back again, but it actually breaks the sudo program:
```

chmod u+w /etc/sudoers
echo "new line" >> /etc/sudoers
chmod u-w /etc/sudoers

```

After I run this script, I get the following error when I try to run sudo again: /etc/sudoers is mode 0640, should be 0440.

Is there any way to change the /etc/sudoers file programmatically ?

Thank you.


As root, you don't need write permission on the file to edit it.

Simply backup the file and append it:
```
cp /etc/sudoers /etc/sudoers.bak
echo "whatever" >> /etc/sudoers
```

or

```
sudo cp /etc/sudoers /etc/sudoers.bak
echo "whatever" | sudo tee -a /etc/sudoers
```

A safer approach would be to create a copy (and a backup) of the file, change the permissions of the copy, edit it, change the permissions back to 0440 on it and overwrite the original file with the copy.

```
#!/bin/bash

if [ -e /etc/sudoers.tmp -o "$(pidof visudo)" ]; then 
  echo "/etc/sudoers busy, try again later"
  exit 1
fi

cp /etc/sudoers /etc/sudoers.bak
cp /etc/sudoers /etc/sudoers.tmp

chmod 0640 /etc/sudoers.tmp
echo "whatever" >> /etc/sudoers.tmp
chmod 0440 /etc/sudoers.tmp

mv /etc/sudoers.tmp /etc/sudoers

exit 0
```

---

### Post by guillaumev on 2009-12-11
Hi,

Thanks a lot for your answers !

sisco311 > Your script works perfectly !

---

