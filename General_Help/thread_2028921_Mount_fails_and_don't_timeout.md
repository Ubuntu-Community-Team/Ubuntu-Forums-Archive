---
title: "Mount fails and don't timeout"
date: 2012-07-19
forum: General Help
---

### Post by Dimas on 2012-07-19
I've a script that runs every 30m and check if /mnt/controlurg is mounted. If not, it tries to mount it and get some files from it (it's a Windows drive). Before 12.04 I didn't had problems but now when the script can't mount (for any reason) the remote drive the mount command don't end and keeps as a background process. And even worst, a new zombie background mount process is created every 30m and the CPU Load Average is getting high (now is 44%!!).

Checking for running processes I get multiple entries like that:
root     29458 29420  0 08:35 ?        00:00:00 mount /mnt/controlurg
root     29459 29458  0 08:35 ?        00:00:00 /sbin/mount.cifs //controlurg/c$ /mnt/controlurg -o rw,noauto,user=root,passwd=glesbolan,utf8

- How can I kill that processes? "kill -9 29459" doesn't work.
- Why these processes don't timeout? How can I kill this failed mounts automatically?

Running Ubuntu Server 12.04 64

Thx

---

### Post by hal8000 on 2012-07-19
Start the script at a terminal
e.g.

/usr/bin/myscript.sh

replacing with corect path and scriptname.
Does it mount the remote filesystem when started from the terminal?

I would also post the contents of your script, if its bash, there is  probably a way to add timeout.

---

### Post by Dimas on 2012-07-19
In fact if now I execute "mount /mnt/controlurg" it doesn't do nothing until I press Ctrl+C... Maybe because there are multiple background processes like that and I can't kill it. I can't restart the server now.. :(

The interesting fragment of /opt/scripts/sftpcont.shl:

```

 cat $SCRIPT/computers.dat | while read line
 do
  echo `date "+%Y/%m/%d %H:%M:%S"` ": Copying to ${line} with samba"
  isalive=`ping -q -c1 $line| grep "1 received" |wc -l`
  if [ $isalive!= "0" ]
   then
    mount /mnt/$line
    rm /mnt/$linea/contingenciasap/*
    cp $SCRIPT/fitxers/sapfitcrip.zip /mnt/$line/contingenciasap
    umount /mnt/$line
  fi
 done

```

I have tried to mount the problematic remote folder in another server with Ubuntu 12.04 and it works:

```
/sbin/mount.cifs //controlurg/c$ /mnt/controlurg -o rw,noauto,user=root,passwd=*****,utf8
```

---

### Post by Dimas on 2012-07-20
Nobody? :(

---

