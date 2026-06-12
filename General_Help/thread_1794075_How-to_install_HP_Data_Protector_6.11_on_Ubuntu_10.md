---
title: "How-to install HP Data Protector 6.11 on Ubuntu 10.04 LTS 64 bits"
date: 2011-06-30
forum: General Help
---

### Post by ericto26 on 2011-06-30
Assure than the DNS name of the client and reverse IP match

```
sudo hostname -f
```

Install RPM and XINETD

```
sudo apt-get update
sudo apt-get install rpm xinetd
```

Modify /usr/bin/rpm with 'force-debian'
```
sudo mv /usr/bin/rpm /usr/bin/rpm-old
```
Edit  /usr/bin/rpm and copy the script bellow and paste it.
```
#!/bin/sh
/usr/bin/rpm-old --force-debian $@

```
save and change the right
```
chmod 755 /usr/bin/rpm
```
Comment in /etc/services the line
```
#rplay     5555/udp   # RPlay audio service
```
Get the HP-DATAPROTECTOR file: Software_HP_DP_6.11_for_HP_UX_PA_B6960_15008_01.tar.gz
```
tar xvfz Software_HP_DP_6.11_for_HP_UX_PA_B6960_15008_01.tar.gz B6960-15008-01/LOCAL_INSTALL/ B6960-15008-01/hpux_pa/DP_DEPOT/DP_A0611_UX11x_IS.sd_depot
```
OR also you can get the DP file over SSH as:
```
ssh login@server_where_is_the_file "cat /directory/Software_HP_DP_6.11_for_HP_UX_PA_B6960_15008_01.tar.gz" |tar xfzv - B6960-15008-01/LOCAL_INSTALL/ B6960-15008-01/hpux_pa/DP_DEPOT/DP_A0611_UX11x_IS.sd_depot
```
Install the DP Agent:
```
cd B6960-15008-01/LOCAL_INSTALL/
sudo ./omnisetup.sh -install da
```
You should get the message:
```
Data Protector software package successfully installed
  Client was not imported into the cell.
  Please perform the Import manually

  Installation/Upgrade session finished.
```

Check if your Ubuntu server has EXT4 filesystem.
If yes. Edit /opt/omni/lbin/.util
Goto line 351 and add "-t ext4" as bellow:
```
/bin/df -P -t ext2 -t SFS -t ext -t minix -t xiafs -t reiserfs -t ext3 -t ext4 -t vfat -t vxfs -t xfs 2>/dev/null | sed '1d' | awk '{print $6}'
```

---

