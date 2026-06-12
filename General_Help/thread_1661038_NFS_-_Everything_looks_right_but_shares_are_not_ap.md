---
title: "NFS - Everything looks right but shares are not appearing"
date: 2011-01-06
forum: General Help
---

### Post by horseatingweeds on 2011-01-06
I set up some shares but **df** and Nautilus aren't bringing them up on the other computer. I must be missing something. I'd appreciate any advice - Thanks. 

Here is how I set up the shares on the one system - **"Compaq"**. 

[LIST=1]
[*]Installed nfs-kernel-server
[*]Modified the nts-common and nfs-kernel-server files:
STATDOPTS="--port 32765 --outgoing-port 32766"
RPCMOUNTDOPTS="-p 32767"
(Do i need to do this on the client as well???)
[*]Opened ports 111, 2049, and 32765:32767
[*]Restarted nfs-kernel-server
[*]In shares-admin I added a couple things, including my ~/ directory, then ran **exportfs -r**
[*]Installed nfs-common on the other system - "ASUS".
[/LIST]
When I run **sudo exportfs** on Compaq I see the two file systems I shared.

On the other system - "ASUS" - I don't see the shares, not in Nautilus or running **df**. 

On Compaq, the one I'm trying to share from, I've confirmed everything is running:

ben@ubu-compaq:~$ service nfs-kernel-server status
nfsd running
ben@ubu-compaq:~$ ps -e | grep mountd
 7111 ?        00:00:00 rpc.mountd
ben@ubu-compaq:~$ rpcinfo -p localhost | grep nfs
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs 

I've also run rpcinfo on the ASUS system but with the IP address of Compaq, getting the same results. Which is good right? 

I can ping back and forth. I've successfully run SSH on the ASUS machine from the Compaq machine. I'm not sure what to do now. Could this be a permissions issue? I'm using the fist user on each system. Any advice would be appreciated.

---

### Post by gmargo on 2011-01-06
What command are you using on the ASUS to mount the NFS filesystems?

---

### Post by horseatingweeds on 2011-01-06
Thanks gmargo, I've got things better understood now. As usual, Linux was working properly, but I didn't know it. 

I used the mount command like so:
sudo 192.168.0.197:/home /compaq.home

Things work, in that I can see the file hierarchies and open most files. On strange thing is though, I can't open Compaq's document files one ASUS, but I can the other way around. OpenOffice hangs trying to open them.

---

