---
title: "Ubuntu NFS problem with older Redhat Linux"
date: 2010-05-03
forum: General Help
---

### Post by KDMerrill on 2010-05-03
Greeting Ubuntu Lovers,

I have 2 Linux boxes; Host-1 (an older box running Redhat 7.3), and Host-2 running 10.04 (was 9.x prior to yesterday).  I had NFS running perfectly between them, but it stopped working a few weeks ago with a 9.x update.  Here are the circumstances:

On NFS Server (Host-1) in /etc/exports:

  # Setup 12/14/2009
  /home/DocShare      Host-2(rw,no_root_squash)
  /usr/MP3                 Host-2(rw,no_root_squash)

in hosts.allow:
   # hosts.allow    This file describes the names of the hosts which are
   #        allowed to use the local INET services, as decided
   #        by the '/usr/sbin/tcpd' server.
   #
   portmap:    192.168.1.
   ALL:        192.168.1.

running exportfs -av yields normal results:
   exporting Host-2:/home/DocShare
   exporting Host-2:/usr/MP3
   reexporting Host-2:/home/DocShare to kernel
   reexporting Host-2:/usr/MP3 to kernel

============================================
== however - when I try to mount these from Host-2 as follows: ==

    sudo mount -o rw Host-1:/usr/MP3 /mnt/MP3

I get the following error:

   mount.nfs: mount to NFS server 'Host-1:/usr/MP3' failed: RPC Error: Program not
   registered

Running rpcinfo -p Host-1 yields:
      program vers proto   port
       100000    2   tcp    111  portmapper
       100000    2   udp    111  portmapper
       100024    1   udp   1024  status
       100024    1   tcp   1024  status
       391002    2   tcp   1025  sgi_fam

I am pulling what is left of my hair out trying to figure out ~WHY~ I can no longer mount these two shares??  It appears to me that the server side (Host-1) is working correctly.  Granted Host-1 is running a VERY old Linux (Redhat 7.3), but it is old hardware, and it is stable so I hate to mess with it too much.  

Does anyone have any experience like this,...and any advice on how to fix and get re-working?

Any help would be GREATLY appreciated.

Kevin in Centreville, VA

---

