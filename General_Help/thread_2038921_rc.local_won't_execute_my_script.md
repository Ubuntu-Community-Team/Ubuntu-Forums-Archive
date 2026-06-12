---
title: "rc.local won't execute my script"
date: 2012-08-07
forum: General Help
---

### Post by Jimboland on 2012-08-07
This is my rc.local:

[I]#!/bin/sh
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

sh /automountnas.sh

exit 0 [/I]

The script I want to mount is currently in my root "/" directory because I tried everything else and it never worked( and it still doesn't!)

When I mount the script from the terminal it works, so I did something good :)
But when I try to automount it with rc.local it won't start. I tried to add **"> /test.log"** behind **sh /automount.sh** to see what happpend but when I open the file its empty, but al least i'm sure the line is executed.

I tried to delete the **"-e"** from **#!/bin/sh** but that did't work either.

Then I saw rc.local is a common problem in Ubuntu, so I came here to see if somebody cal tell me what the problem could be.

---

### Post by Statia on 2012-08-07
Maybe you could try instead of making rc.local execute your script putting the contents of your script IN rc.local.

---

### Post by Jimboland on 2012-08-07
Nope, just tried that now, didn't work.

---

### Post by Toz on 2012-08-07
Care to share the contents of your script?

---

### Post by Jimboland on 2012-08-07
Offcource!

#!/bin/bash
X="myusername"
Y="mypass"
sudo mount -t cifs //192.168.10.104/volume_1 ~/nas/ -o username=$X,password=$Y,domain=workgroup

---

### Post by Toz on 2012-08-07
First of all, there is no need for sudo if you are running the script in /etc/rc.local - it runs with root privileges by default.

Secondly, you are mounting to ~/nas. Is that directory accessible prior to you logging in? If, for example, you have encrypted your home directory, then you won't have access to that mount point until you have logged in and unencrypted it. If this is the case, you are better to mount it elsewhere and link to it from your home directory.

---

### Post by Jimboland on 2012-08-07
I removed sudo and tried again but it didn't work. And my home directory is not encryped.

rc.local script looks like this at the moment:

[U]#!/bin/sh 
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

#!/bin/bash
X="myusername"
Y="mypass"
mount -t cifs //192.168.10.104/volume_1 ~/nas/ -o username=$X,password=$Y,domain=workgroup

exit 0[/U]

I tried **#!/bin/sh** and **#!/bin/sh -e** but neither worked for me.

---

### Post by papibe on 2012-08-07
Hi Jimboland.

Any special reason to do this on rc.local.

I would set the mount on /etc/fstab so that it is mount automatically at the moment the OS mount partitions.

Note that the syntax would be different.

Regards.

---

### Post by Toz on 2012-08-07
> **Jimboland said:**
> I removed sudo and tried again but it didn't work. And my home directory is not encryped.

rc.local script looks like this at the moment:

[U]#!/bin/sh 
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

#!/bin/bash
X="myusername"
Y="mypass"
mount -t cifs //192.168.10.104/volume_1 ~/nas/ -o username=$X,password=$Y,domain=workgroup

exit 0[/U]

I tried **#!/bin/sh** and **#!/bin/sh -e** but neither worked for me.

Try changing ~/nas to the full path of your mount point. If the script is running as root, then ~/nas will point to root's home directory, not yours.

papibe's suggestion is a good one as well. Or you can try automount.

---

### Post by Jimboland on 2012-08-07
I tried momunting it with fstab using this guide below but that didn't work.

[http://r3dux.org/2009/02/how-to-mount-a-nas-in-linux-via-samba/](http://r3dux.org/2009/02/how-to-mount-a-nas-in-linux-via-samba/)

Then I tried:

*Try changing ~/nas to the full path of your mount point. If the script is running as root, then ~/nas will point to root's home directory, not yours.*

That worked!

Here is what I did:

[I]#!/bin/sh 
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

mount -t cifs //192.168.10.104/volume_1 home/jimmy/nas/ -o username=myusername,password=mypass,domain=workgroup

exit 0 [/I]

My nas is now automounted in my system!:D

Thanks for your help guys!! 
You made me very happy.

---

