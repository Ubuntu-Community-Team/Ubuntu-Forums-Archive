---
title: "Recover /etc/resolvconf/run/resolv.conf file"
date: 2010-03-29
forum: General Help
---

### Post by jaikiran on 2010-03-29
Hello everyone,

I am using Ubuntu 9.04. This morning, while fiddling with my VPNC, I mistakenly  deleted the /etc/resolvconf/run/resolv.conf instead of /etc/resolv.conf file. I was in the process of doing this:

```
sudo rm -rf /etc/resolv.conf
sudo ln -s /etc/resolvconf/run/resolv.conf
```But ended up doing:
```

sudo rm -rf /etc/resolvconf/run/resolv.conf
```Is there any way I can recover that deleted /etc/resolvconf/run/resolv.conf file?

Thank you.

---

### Post by r.stiltskin on 2010-03-29
Just create a new resolv.conf file and save it there.  Many people use
```
nameserver 4.2.2.1
nameserver 4.2.2.6

```

Other free public nameservers are listed here:[http://theos.in/windows-xp/free-fast-public-dns-server-list/]("http://theos.in/windows-xp/free-fast-public-dns-server-list/")

---

### Post by jaikiran on 2010-03-29
Thank you! That helped :)

---

### Post by garvinrick4 on 2010-03-29
Is not your etc/resolv.conf generated everytime you connect to a domain.

in Live CD. something like this.

Mount your drive you want to add etc/resolv.conf to.

sudo mkdir /media/lucid
sudo mount /dev/sda5 /media/lucid
sudo cp /etc/resolv.conf /media/lucid/etc/resolv.conf

You now have a internet connection in lucid.
_________________________________
sudo chroot /media/lucid

now you are root.
__________________________________
apt-get update && apt-get upgrade

upgraded your lucid system.
_____________________________________
ctrl/d

out of root.
______________________________________
sudo umount /media/lucid

unmounted you file system
====================
This is all predicated on my label of lucid and my sda5.
You have to use your label and partition

---

