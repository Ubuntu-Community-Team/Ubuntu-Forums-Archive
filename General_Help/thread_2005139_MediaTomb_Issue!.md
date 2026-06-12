---
title: "MediaTomb Issue!"
date: 2012-06-17
forum: General Help
---

### Post by kindrudekid on 2012-06-17
I want to install Mediatomb

i have two HDD a small 120 gb and a 1tb drive

the 1 tb drive has 3 partition and is encrypted with truecrypt

when i run the Mediatomb it can read the drives on the 120 gb but not on the 1 tb

the 1tb drive is mounted on startup using a script also i have added truecrypt to the sudoers permission if it helps

the permision on all 1 tb truecrypt mount pops up as my username where as the 2 partition from 120 gig has nobody

i just got a Asus TF300T and i wanna stream media using DLNA/UPnP

---

### Post by matt_symes on 2012-06-17
Hi

> when i run the Mediatomb it can read the drives on the 120 gb but not on the 1 tb

I assume it can see the 1 Tb drive and it is mounted but it is not reading the files ?

Are you sure the drive is being decrypted correctly at boot up ?

Can you post your script.

If you mount the drive manually does Mediatomb see the files on the drive ?

If you run the script manually does Mediatomb see if the files on the drive ?

How are you running the script at start up ? Is it being decrypted before Mediatomb runs ?

Please supply much more information.

Kind regards

Where are you mounting the drive ?

---

### Post by kindrudekid on 2012-06-17
This Files is Stored in ~./TrueCrupt/tcam.sh

And ran using Startup manager on Xubuntu and is located at ~/.config/autorstart

```

# Required-Start:    $remote_fs $syslog $time
# Required-Stop:     $remote_fs $syslog $time
# Default-Start:     2 3 4 5
# Default-Stop:      1
# Short-Description: Encryted volumen support
# Description:       tc provide support for mounting encrypted
#                    with truecrypt volumens
### END INIT INFO

truecrypt --mount /dev/sdb1 /media/ctb -p "PASSWORD"
truecrypt --mount /dev/sdb2 /media/dtb -p "PASSWORD"
truecrypt --mount /dev/sdb3 /media/etb -p "PASSWORD"

```



Also if i halt MediaTOMB service and start it manually from Command Line using sudo permissions it reads

Yes i can read the drives as the entire drives are NFS shared and i can access it from Windows/Ubuntu on laptop



Drives are mounted at /media/

Permissions on the encrypted folders/mounts are my username only


where as the other mounts/drives are nobody

Can i run the script as user nobody?


but i often update that machine remotely and when i reboot i want it to mount automatically!

---

### Post by matt_symes on 2012-06-17
Hi

> **kindrudekid said:**
> And ran using Startup manager on Xubuntu and is located at ~/.config/autorstart
...

Also if i halt MediaTOMB service and start it manually from Command Line using sudo permissions it reads

Yes i can read the drives as the entire drives are NFS shared and i can access it from Windows/Ubuntu on laptop


I think that the decryption is happening after Mediatomb is starting and i think that may be your problem (although i'm not 100% sure at this point).

The fact that if you restart the Mediatomb daemon it can read the drive and the fact you can view the drive normally, is what makes me think this. That is where i would start looking.

You could try to create an upstart job that decrypts the drive after mounting but before starting the Mediatomb daemon.

I'm not 100% sure if this is your problem but it is where i would start looking.

Kind regards

---

### Post by kindrudekid on 2012-06-20
i dont know i give up argh!

---

