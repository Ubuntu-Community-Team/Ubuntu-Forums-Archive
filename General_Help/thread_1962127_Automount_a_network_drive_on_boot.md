---
title: "Automount a network drive on boot"
date: 2012-04-20
forum: General Help
---

### Post by alanshort on 2012-04-20
[FONT=Arial][SIZE=2]Hey guys, 

i have a script which mounts a external drive connected to my router.

#!/bin/bash
echo "Mounting Elements01 Network Drive"
sudo mount -t cifs //10.0.1.1/Elements01 -o uid=1000,gid=1000,iocharset=utf8,dir_mode=0775,username=xxx,password=xxx, /media/Elements01/

it works just fine.

What I would like is for this script to be run at boot or login so it automounts the drive and i don't have to keep running the script manually following login.

I've tried adding an entry to /etc/init.d/ and running update-rc.d[/SIZE][/FONT][FONT=monospace][FONT=Arial][SIZE=2] so the script runs as root, however when booting, the drive is not mounted. I've run the script link to the script located in [/SIZE][/FONT][/FONT][FONT=Arial][SIZE=2]/etc/init.d/ as root and it works fine.

I'm guessing that the mount script may be trying to run before the network is up and therefore failing.... maybe.

please could someone guide me as to the best way of getting this network drive mounted at boot time ?

Cheers, 
Alan
[/SIZE][/FONT][FONT=monospace][/FONT]

---

### Post by raja.genupula on 2012-04-20
[http://www.automaticable.com/2008-01-18/how-to-mount-a-network-drive-in-ubuntu/](http://www.automaticable.com/2008-01-18/how-to-mount-a-network-drive-in-ubuntu/)

---

### Post by Morbius1 on 2012-04-20
> I'm guessing that the mount script may be trying to run before the network is up and therefore failing.... maybe.

please could someone guide me as to the best way of getting this network drive mounted at boot time ?Given the fact that you are mounting it with yourself as owner my recommendation is to use gigolo: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

Gigolo waits until both the client and also the server is ready before it mounts.

Anywho, if you think it's a timing issue with the network then place your script here:
```
/etc/network/if-up.d
```Any script placed within that directory will only run after the network is up.

---

