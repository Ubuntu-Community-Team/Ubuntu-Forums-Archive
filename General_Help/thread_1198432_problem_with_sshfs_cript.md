---
title: "problem with sshfs cript"
date: 2009-06-27
forum: General Help
---

### Post by WitchCraft on 2009-06-27
Hi, I have a problem with a bash script:

When I do this in a terminal:
```

/sbin/mount.vboxsf -rw cadmin /mnt/cadmin
sshfs root@prename-familyname.ch:/ /mnt/sshfs

```then it mounts the two drives

but when I do the same in the bash script below, double click on it and say run in terminal, then it doesn't mount the sshfs. cadmin will be mounted fine, however.

It doesn't matter if I mount the sshfs before or after the cadmin drive, it does not get mounted... why?

I don't need to input a password, it uses RSA keys

```

#!/bin/bash

mkdir -p /mnt/cadmin
mkdir -p /mnt/sshfs


# fails - whatever
# modprobe vboxvfs
# modprobe vboxfs
#mount -t vboxfs cadmin /mnt/cadmin
echo "Mounting drive c"
/sbin/mount.vboxsf -rw cadmin /mnt/cadmin
echo "Mounting sshfs"
sshfs root@prename-familyname.ch:/ /mnt/sshfs

```

Using
sshfs [email]root@prename-familyname.ch[/email]:/ /mnt/sshfs -o IdentityFile=/home/meeeeeeee/.ssh/id_rsa
doesn't make any difference...

---

### Post by WitchCraft on 2009-06-27
Revision 1, but still the same problem...

```

#!/bin/bash

mkdir -p /mnt/cadmin
mkdir -p /mnt/sshfs


# fails - whatever
# modprobe vboxvfs
# modprobe vboxfs
#mount -t vboxfs cadmin /mnt/cadmin

echo "Making sure drives are unmounted..."
umount cadmin 2>/dev/null
umount sshfs 2>/dev/null
kill `ps -ef | grep "username" | grep "sshfs" | sed 's/root *//' | cut -d " " -f 1` 2>/dev/null



echo "Mounting drive C:\\"
if !( /sbin/mount.vboxsf -rw cadmin /mnt/cadmin ); then
  echo "Error: Mounting failed!"
  exit 1
else
  echo "Mounting successful."
fi

echo "Mounting Synology filesystem as root"
#sshfs root@prename-familyname.ch:/ /mnt/sshfs
#sshfs root@prename-familyname.ch:/ /mnt/sshfs -o IdentityFile=/home/username/.ssh/id_rsa

if !( sshfs root@prename-familyname.ch:/ /mnt/sshfs -o IdentityFile=/home/username/.ssh/id_rsa & ); then
  echo "Error: Mounting failed!"
  umount cadmin 2>/dev/null
  exit 1
else
  echo "Mounting successful."
fi
sleep 5

```

---

### Post by WitchCraft on 2009-06-27
OK, the problem seems to be that sshfs quits when the bash script exits...
In the 5 seconds the bash script sleeps, sshfs is mounted...

How can I make sshfs persistent over the lifetime of the script?

---

### Post by WitchCraft on 2009-06-27
OK, after f*ing 3 hours, I could solve the problem...

It is not possible to do this in bash, since user access to the spawn command from the command line has been removed for whatever reason.

You need to use a python script:

```

#!/usr/bin/python

import pexpect
import time
import os
import sys


#apt-get install python-pexpect

command = "sshfs root@prename-familyname.ch:/ /mnt/sshfs -o IdentityFile=/home/username/.ssh/id_rsa"

def start_sshfs():
 try:
  sshfs = pexpect.spawn(command)
  #time.sleep (10)
  sshfs.expect (pexpect.EOF)

 except Exception, e:
  print str(e)
  sys.exit()


def main ():
 print "Establishing mountpoints..."
 os.popen("mkdir -p /mnt/cadmin 2>/dev/null")
 os.popen("mkdir -p /mnt/sshfs 2>/dev/null")
 
 print "Making sure drives are unmounted..."
 os.popen("umount cadmin 2>/dev/null")
 os.popen("fusermount -u sshfs 2>/dev/null")
 #os.popen("umount sshfs 2>/dev/null")
 #kill `ps -ef | grep "username" | grep "sshfs" | sed 's/root *//' | cut -d " " -f 1` 2>/dev/null
 
 print "Mounting drive C:\\"
 iReturnValue = os.system("/sbin/mount.vboxsf -rw cadmin /mnt/cadmin") # store the exit code.
 # fails - whatever
 # modprobe vboxvfs
 # modprobe vboxfs
 # mount -t vboxfs cadmin /mnt/cadmin
 
 
 if (iReturnValue):
  print "Error: Mounting failed!"
  sys.exit()
 else:
  print "Mounting successful."
 
 print "Mounting Synology filesystem as root"
 start_sshfs()
 # Wait for 3 seconds for reading potential error messages
 time.sleep(3)
 #umount sshfs cadmin
 

if __name__ == '__main__':
 main ()

```

---

### Post by WitchCraft on 2011-06-05
For the usage with password, see this file:
[http://ubuntuforums.org/showthread.php?t=135113](http://ubuntuforums.org/showthread.php?t=135113)

And for automation on bootup, see:
[http://pwnguin.net/mount-sshfs-at-boot.html](http://pwnguin.net/mount-sshfs-at-boot.html)

And mounting a SFTP-Folder:
[http://blog.damontimm.com/how-to-mount-a-sftp-folder-ssh-ftp-on-ubuntu-linux-using-sshfs-fuse/](http://blog.damontimm.com/how-to-mount-a-sftp-folder-ssh-ftp-on-ubuntu-linux-using-sshfs-fuse/)

---

