---
title: "Automatic partition mounting stopped working after upgrade"
date: 2010-05-04
forum: General Help
---

### Post by drunkenbrawler on 2010-05-04
Hello everyone,
I'm an Ubuntu/Kubuntu user for a while now and i hav Kubuntu 9.10 with ubuntu-desktop installed.

I have two hard disks and i had one of the partitions mounted automatically while startup. I did that by reading the first method posted here
[HTML]https://help.ubuntu.com/community/AutomaticallyMountPartitions[/HTML]

It was working good till i did the distribution update to Kubuntu 10.04. After the upgrade while startup, a message is displayed on the screen saying
> "Disk to be mounted at /media/miscellaneous is not ready or is not there.
  Continue waiting or press S to skip mounting or M for manual recovery"

I dont know what to do. I have to skip and then mount the partition manually. I think the entry i added in
> /etc/fstab is still there.

any help will be greatly appreciated.

---

### Post by drunkenbrawler on 2010-05-04
Problem solved guys,

I think after upgradation, the names of my hdds were interchanged. "sda" became "sdb" and vice-versa. saw that in fdisk and then edited fstab entry. Everything works good now.

Sorry to bother you.

---

