---
title: "Rebuild md RAID array after OS disk failure"
date: 2010-12-19
forum: General Help
---

### Post by pormogo on 2010-12-19
So a few weeks ago after a move I went to setup my linux box and found that the OS drive had finally died. It was an extremely old WD raptor drive in a hot box full of drives so it was really only a matter of time before it just quit on me. Normally this wouldn't be such a big deal however I had just recently constructed an md RAID5 array of 3 1TB disks to act as an NFS mount for basically all of my important files. Maybe 2-3 weeks before the failure I had finished moving all of my most important stuff onto that array. Now I know that the array is intact. All the required data is sitting on those disks. Since only the OS level disk failed on me I should be able to get a new disk in there, reinstall ubuntu and then rebuild that array. My question is, how exactly do I go about doing that with mdadm? 

Do I create the array from the /dev character devices like when I initially built the array? Is there a specific way that I am supposed to resync/rebuild the array with madadm? Thanks in advance for any help you guy would be able to provide.

---

### Post by Reinkens on 2010-12-19
I had the same thing happen a little while ago, here is what I did to get the raid going again.

* replace the dev/mount locations where appropriate
```
sudo apt-get install mdadm
sudo mdadm --assemble /dev/md0 /dev/sda /dev/sdb /dev/sdc
sudo -s
sudo echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
sudo mdadm --detail --scan >> /etc/mdadm/mdadm.conf

mkdir /media/raid

#add to /etc/fstab
/dev/md0 /media/raid auto defaults 0 3
```

---

### Post by tjhart85 on 2011-04-08
> **Reinkens said:**
> I had the same thing happen a little while ago, here is what I did to get the raid going again.

* replace the dev/mount locations where appropriate
```
sudo apt-get install mdadm
sudo mdadm --assemble /dev/md0 /dev/sda /dev/sdb /dev/sdc
sudo -s
sudo echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
sudo mdadm --detail --scan >> /etc/mdadm/mdadm.conf

mkdir /media/raid

#add to /etc/fstab
/dev/md0 /media/raid auto defaults 0 3
```

Haven't had my OS drive die (yet), but damn, that looks remarkably easy to recover!

---

