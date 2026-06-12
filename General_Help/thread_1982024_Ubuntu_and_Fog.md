---
title: "Ubuntu and Fog"
date: 2012-05-17
forum: General Help
---

### Post by icemannz on 2012-05-17
Hi all,
I  have a Fog Server and I have setup Ubuntu to run from the Fog Server via PXE Network Boot.
But I cannot save any settings, it boots up and works ok but I cannot make any changes.
I am new to this so it is proabably something fairly simple and any help would be appreciated.
To setup Ubuntu under fog, this is what I did
 
 sudo nano /tftpboot/aviad/menus/linux.cfg
  Add in the following lines:
  LABEL Ubuntu Livecd
  KERNEL aviad/linux/ubuntu/casper/vmlinuz
  APPEND root=/dev/nfs boot=casper netboot=nfs nfsroot=192.168.20.7:/tftpboot/aviad/linux/ubuntu initrd=/aviad/linux/ubuntu/casper/initrd.lz quiet splash –
   
    sudo mkdir -p /tftpboot/aviad/linux/ubuntu
  copy the contents of the Ubuntu CD into that directory
  sudo nano /etc/exports
  To share the ubuntu directory via NFS, add this to the end of the file:
  /tftpboot/aviad/linux/ubuntu   *(rw,sync,no_wdelay,insecure_locks,no_root_squash,insecure)
  To restart the NFS server:
  sudo /etc/init.d/nfs-kernel-server restart

---

### Post by icemannz on 2012-05-18
Bump
No ideas anyone ?

---

### Post by MrMisterio on 2012-12-22
Hello, I am just working on this and wanted to thank you for giving me a starting point. I see you started this early in the year, better late than never... Here's what you need to add to get yours working:
 
LABEL Kubuntu x64
        KERNEL kubuntu_x64/casper/vmlinuz boot=casper toram splash
        APPEND root=/dev/nfs boot=casper netboot=nfs nfsroot=192.168.2.127:/tftpboot/kubuntu_x64 initrd=kubuntu_x64/casper/initrd.lz quiet splash –
        MENU Kubuntu x64
        TEXT HELP
        Run Kubuntu x64
        ENDTEXT
 
ref: [https://wiki.ubuntu.com/BootToRAM](https://wiki.ubuntu.com/BootToRAM)

---

