---
title: "nfs cannot mount"
date: 2009-12-10
forum: General Help
---

### Post by siuchi on 2009-12-10
I have two computer, but i cannot connect nfs from client computer to server. Anyone can help? Below is details:

nfs server running ubuntu 8.04 (192.168.9.12), 
client running 9.04 (192.168.9.11).

Showmount -e 192.168.9.12   (Run from 192.168.9.11)
showmount -e 192.168.9.12
Export list for 192.168.9.12:
/home/iso                         192.168.9.0/255.255.240.0

showmount -a 192.168.9.12    (Run from 192.168.9.11)
All mount points on 192.168.9.12:
192.168.4.205:/home/iso
192.168.7.2:/home/iso
192.168.9.11:/home/iso
192.168.9.11:/home/operationsbackup/operations
192.168.9.14:/home/iso
192.168.9.25:/home/iso
192.168.9.25:/home/iso/ubuntu-8.10-desktop-i386.iso

sudo mount -tnfs 192.168.9.12:./iso iso/ (run from 192.168.9.11)
mount.nfs: access denied by server while mounting 192.168.9.12:./iso

---

