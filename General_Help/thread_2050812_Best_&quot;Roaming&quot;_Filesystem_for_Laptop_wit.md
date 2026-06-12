---
title: "Best &quot;Roaming&quot; Filesystem for Laptop with SSD"
date: 2012-08-31
forum: General Help
---

### Post by vinsonizer on 2012-08-31
First post, so please be gentle...

I just moved my wife from windows 7 64 to Ubuntu 12.04.1 LTS on her laptop.  During the move I also decided to upgrade to an SSD drive to replace the old HDD.  This all works great, but I am concerned that it will not have enough disk space for her normal usage pattern (lots of photos etc).

What I would like to do is to have a way to allow her to have some of her home directory subfolders (Pictures, Documents, etc) mounted to a location on my home network that I can also backup regularly.  I have a decent desktop with Ubuntu 12.04.1 and a 1TB RAID 1 that should suffice for that.

I've tried autofs using NFS, but it hangs up Nautilus etc. when I am disconnected from the network.  Is there a solution that is more forgiving for a mobile system?  When we travel, i'd like her to still be able to use it for general internet access, etc.

Any pointers would be much appreciated.

---

### Post by BLuFeNiX on 2012-08-31
Have you tried Samba? Also, whatever networked mounting solution you choose, you could look into this if you want to mount it automatically whenever the laptop connects to it's home network: [http://www.techytalk.info/start-script-on-network-manager-successful-connection/#comment-3498](http://www.techytalk.info/start-script-on-network-manager-successful-connection/#comment-3498)

---

### Post by vinsonizer on 2012-08-31
I am very familiar with Samba, just didn't have a hard requirement to support windows networking and didn't know if Samba really had any advantages when that is the case.

That is a very interest link you posted though.  I wasn't aware that network manager had those sort of hooks.  I will definitely give that a shot and post my results.

---

### Post by vinsonizer on 2012-08-31
I've got something that appears to work, using the following in:

/etc/NetworkManager/dispatcher.d/90handle_home_mounts.sh 

```

#!/bin/bash

IF=$1
STATUS=$2

if [ "$IF" == "wlan0" ]
then
    case "$2" in
        up)
        logger -s "NM Script up triggered"
        /bin/ping -c 1 192.168.14.3 > /dev/null && /sbin/mount.nfs nfsserver:/home /nfs/nfsserver/home -ws
        ;;
        down)
        logger -s "NM Script down triggered"
        /bin/umount -a -t nfs -l
        ;;
        pre-up)
        logger -s "NM Script pre-up triggered"
        ;;
        post-down)
        logger -s "NM Script post-down triggered"
        ;;
        *)
        ;;
    esac
fi


```

The key was to use the -l on the umount, which does a nicer unmount of NFS when the wifi connection drops.  From the man page:

```

       -l     Lazy  unmount.  Detach  the filesystem from the filesystem hierarchy now, and cleanup all references to the filesystem as soon as it is not busy any&#8208;
              more.  (Requires kernel 2.4.11 or later.)

```

---

### Post by dcstar on 2012-08-31
> **vinsonizer said:**
> I've got something that appears to work
.......

Then MARK the thread.

---

### Post by dcstar on 2012-08-31
> **vinsonizer said:**
> First post, so please be gentle...

I just moved my wife from windows 7 64 to Ubuntu 12.04.1 LTS on her laptop.  During the move **I also decided to upgrade to an SSD drive** to replace the old HDD.
........

Did you add the "discard" option to the relevant /etc/fstab line?

---

### Post by vinsonizer on 2012-09-01
I did use the discard option already.  By MARK the thread, i assume you mean mark it as solved, which I already did.

---

