---
title: "system won't boot, won't shut, won't reinstall..."
date: 2011-02-24
forum: General Help
---

### Post by aleatoire on 2011-02-24
hi

a few days ago, my netbook (asus eee) suddenly shutdown because the battery was too low - I had  an Ubuntu 10.04 LTS on it, in dual boot with windows

at the reboot, I had :

```
mount: mounting /sys on /root/sys failed: No such file or directory
  mount: mounting /proc on /root/proc failed: No such file or directory
  Target filesystem doesn't have requested /sbin/init.
  No init found. Try passing init = bootarg.
```

Windows is still booting and working fine - as for Ubuntu, I've tried various things at first :

```
sudo fsck -f -y /dev/sda5

sudo os-prober

sudo fuser -v -m /dev/sda5

``` but the answers where (sorry, French computer) :

```
a job is pending on dev/sda5

Système de fichier monté ou ouvert en mode exclusif par un autre
programme ?

Impossible d'obtenir les stat du fichier /proc/4328/fd/33: Panne d'accès au fichier NFS
```So I tried more things :

- booting on a live usb 10.04 > freeze at the beginning (on the screen where dots are lighted under the Ubuntu logo)

- booting on a live usb 10.10 > works fine, allowed me to see that an unknown process is blocking /dev/sda5 so that I can't stop it, mount or unmount sda5

- reinstall ubuntu from the live usb 10.10 > freeze at the beginning (on the screen when we're offered the option of downloading upgrades, which I didn't choose)

- booting on a live Fedora 14 > works fine but still the same answer when I try to check sda5 with fsck ("device busy", then chen I try to unmont it "the device is not mounted")

- booting on a live usb sysresccd 

> in graphic mode, gparted turns on loop on "scanning all devices" and bever finds anything (I've treid various solutions found on the web to stop that loop but they didn't work) 

> in a terminal, same answers as previously :

```
root@sysresccd /root % fsck -f -y /dev/sda5
fsck from util-linux-ng 2.18
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sda5
Filesystem mounted or opened exclusively by another program?
root@sysresccd /root %
``` then if I try

```
root@sysresccd /root % fuser -v -m /dev/sda5
                     USER        PID ACCESS COMMAND
/dev/sda5:           root       2153 F.... mdadm
                     root       2314 F.... mdadm

root@sysresccd /root % fuser -k -TERM -v -m /dev/sda5
                     USER        PID ACCESS COMMAND
/dev/sda5:           root       2153 F.... mdadm
                     root       2314 F.... mdadm
```

I must say I quite don't know what to try next... I've king of given up getting my data back, but I can't seem to even reinstall the system... The problem is also that the system will never shut down correctly when I've been working on the live usbs : when I do

```
shutdown -h now
```

it does start exiting, but it then freezes indefinitely at some point

Any idea will be very welcome...

thanks

aleatoire

---

