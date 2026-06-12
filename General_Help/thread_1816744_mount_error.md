---
title: "mount error"
date: 2011-08-02
forum: General Help
---

### Post by dandeliondream on 2011-08-02
I am trying to do a mount on the client machine.
 
i type on the client machine "sudo mount 192.168.126.140:/data /home/sally/data" but it returns an error.
 
Error:
mount: wrong fstype, bad option, bad superblock on 192.168.126.140:/data, missing codepage or helper program, or other error(for several filesystem e.g. nfs, cifs) you might need a /sbin/mount.<type> helper program) In some cases useful info is found in syslog -try dmesg | itail or so.
 
I search the internet and realised i need to install portmap and nfs-common, so i tried a sudo apt-get install nfs-common portmap
 
but I am unable to download it. What do i do?
 
I am running VMware player with ubuntu10.04 installed -both client and server.

---

### Post by skinnyquiver on 2011-08-02
can you post the error that you get when you run 
sudo apt-get install nfs-common

Thanks,

---

### Post by dandeliondream on 2011-08-02
Please see image for error message.
[IMG]http://www.zumodrive.com/file/preview_content/520922834?key=dT5bMDE1OT&last_modified=1312328434&revision=1[/IMG]
 
> **skinnyquiver said:**
> can you post the error that you get when you run 
sudo apt-get install nfs-common
 
Thanks,

---

### Post by skinnyquiver on 2011-08-03
run
apt-get update
apt-cache search nfs
is nfs common in that list?

---

### Post by dandeliondream on 2011-08-03
It works now. Thank you for your help!:KS
 
> **skinnyquiver said:**
> run
apt-get update
apt-cache search nfs
is nfs common in that list?

---

