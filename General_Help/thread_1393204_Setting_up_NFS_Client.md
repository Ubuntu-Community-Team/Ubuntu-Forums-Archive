---
title: "Setting up NFS Client"
date: 2010-01-29
forum: General Help
---

### Post by uaebuntu on 2010-01-29
I bought a QNAP 219P NAS as it was Linux "Compatible" what it lacks is the instructions on how to install under Linux.

I've set up the NAS on the network, have given it a server name, and can connect to it through my web browser, everything appears to be OK with it.

What I can't do, as I'm new to Linux, is get the PC to mount the drive.

I have installed nfs-common and portmapper through synaptic package manager and I run Ubuntu 9.10 64 bit. If someone can help walk me through the setup so the NAS can be used by multiple clients (PCs) and is always there on logon I would be eternally greatful

---

### Post by uaebuntu on 2010-01-30
I've made a bit of progress. 

Through the web interface to the QNAP I've created a folder "Server" which I've made RW and public access.

I have enabled the NFS services on the QNAP by selecting a menu item.

From my PC I have run

# sudo mount -t nfs 192.168.1.50:/Server /mnt/Server

but get a "can't find mount point" error, so if I could define a mount point I might be able to at least transfer files

I've also tried following the instructions in the sourceforge NFS-HOW TO document but got completely lost trying to do the client set up.

---

### Post by uaebuntu on 2010-02-05
Got some progress.

All to do with the network and permissions in the NFS server in the NAS

First solved the problem by going to static IPs and making one client talk to the server then worked out how to make the server accept ranges of IPs so back to DHCP except for the NFS Server where I fixed the IP at 192.168.1.50, created a number of directories with R/W access such as /Servers 

on the NFS Clients (all Ubuntu 9.10) reconfigured portmap to not bind loopback and created a mount point /NAS/ from root

#sudo -s
#dpkg-reconfigure portmap
#restart portmap
#mkdir /mnt/NAS/

#sudo mount -t nfs 192.168.1.50:/Servers /mnt/NAS/

now works whenever I run it!

Next stage is to work out
 
how to put the mount statement in the start up script so I don't have to type it in each time, 
how to manage my two laptops who may or may not be connected to the nfs server network, and
how to make the mount points appear automatically in the Places dropdown on the desktop

any help on the above gratefully received as I'm new to all this.

---

### Post by louieb on 2010-02-05
Have you seen [HOWTO: NFS Server/Client - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs")

if you make the mount point in /media/<some dir> you will get an icon on the desktop and it will show up in the places menu.

---

### Post by uaebuntu on 2010-02-09
Thanks

Thats the last piece of the jigsaw...

Have edited fstab for the general access and bash for individual users now I can mount things so they show up easily.

---

