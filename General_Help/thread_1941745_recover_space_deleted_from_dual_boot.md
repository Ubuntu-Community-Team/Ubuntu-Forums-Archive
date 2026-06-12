---
title: "recover space deleted from dual boot"
date: 2012-03-16
forum: General Help
---

### Post by alwaysonnet on 2012-03-16
i installed Linux Mint 12 along side of Ubuntu 11.10 on 40G harddisk. But I didn't like Mint and deleted the partition using gparted and updated the grub using a live session. Initially I've allocated 10G for Mint and 30G for Ubuntu.

Is it possible to ~

[LIST]
[*]merge 10G partition into Ubuntu partition.
[*]use as a separate partition to save the files.
[/LIST]

---

### Post by miklcct on 2012-03-16
1. boot from a live media
2. run gparted
3. make the Ubuntu partition 10G larger
4. create a data partition

---

### Post by sudodus on 2012-03-16
> **alwaysonnet said:**
> i installed Linux Mint 12 along side of Ubuntu 11.10 on 40G harddisk. But I didn't like Mint and deleted the partition using gparted and updated the grub using a live session. Initially I've allocated 10G for Mint and 30G for Ubuntu.

Is it possible to ~

[LIST]
[*]merge 10G partition into Ubuntu partition.
[*]use as a separate partition to save the files.
[/LIST]

Yes and yes, it is possible to merge (if it is adjacent to the Ubuntu partition) and it is certainly possible to use as a separate partition.

You can use ***gparted,*** if you want to re-partition or re-format the partition. ***But before doing any editing of partition, you should backup your whole system or at least your personal files*** (documents, pictures, videos ...), because it is risky!

If you 'only' want to use the partition the save files, simply delete all the files of Mint, and start using it :-)

---

