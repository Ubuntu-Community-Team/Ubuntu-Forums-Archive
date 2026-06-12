---
title: "NFS mount does not work"
date: 2010-10-05
forum: General Help
---

### Post by viki__ on 2010-10-05
I try to connect to an NFS server, but i always get the following error message: mount.nfs: an incorrect mount option was specified

The command i am using is the following: sudo mount -t nfs 10.0.0.101:/opt/Java /home/viki/Java/virtualServer

Can you please to help me what can be the issue?

Thanks

---

### Post by fragos on 2010-10-05
Here's what works for me:

I use NFS between my Desktop and Laptop as my server. Both being on the same LAN. On the Laptop server there must be an /etc/exports file with the following. Replace the fields in {} with your information. In my example I'm giving access to the entire home folder tree on the Laptop server. There can be multiple entries giving more clients permission.

/home/{Laptop user} {Desktop hostname}.local(rw)

Run "sudo exportfs -rv" on the Laptop server for the system to read /etc/exports and allow the Desktop client access. You'll need to do this whenever you reboot your Laptop or edit /etc/rc.local and add the line "exportfs -rv" which will then run as root when the system boots.

On the Desktop client create a folder to mount to. In my case I placed that folder in my home folder. You need only do this once as it reusable.

On the Desktop client side I run

sudo mount {Laptop hostname}.local:/home/{Laptop user} /home/{Desktop user}/{folder to mount to}

To un-mount I run

sudo umount {Laptop hostname}.local:/home/{Laptop user} /home/{Desktop user}/{folder to mount to}

You can extrapolate what to do from this working example. I chose not to use fstab to mount and wrote a couple of bash scripts that supply the parameters to the mount and umount commands.

---

### Post by SeijiSensei on 2010-10-06
Try it without the '-t nfs' option and see if that helps.  mount knows that a filesystem named server:/some/path is an NFS mount.  It might be a problem about conflicting NFS versions between the server and client.

Are you in control of the NFS server?  What is the line in /etc/exports that pertains to /opt/Java?

Do you see any errors logged in the server's logs?  Take a look at /var/log/syslog and /var/log/messages to see what's happening on the server.

---

### Post by viki__ on 2010-10-06
On the NFS server in the /etc/exports file the following can be found:
/opt/Java 10.0.0.0/24

I do not see any message in the syslog or in the messages if i try to connect.

---

### Post by luvshines on 2010-10-06
What does showmount -e <server-address> shows ?

---

### Post by viki__ on 2010-10-06
Export list for 10.0.0.101:
/opt/Java 10.0.0.0/24

---

### Post by luvshines on 2010-10-06
And what does verbose for mount say ??

mount -vvv -t ...

---

### Post by viki__ on 2010-10-06
mount: fstab path: "/etc/fstab"
mount: mtab path:  "/etc/mtab"
mount: lock path:  "/etc/mtab~"
mount: temp path:  "/etc/mtab.tmp"
mount: UID:        1000
mount: eUID:       0
mount: spec:  "10.0.0.101:/opt/Java"
mount: node:  "/home/viki/Java/virtualServer"
mount: types: "nfs"
mount: opts:  "noauto,user,udp"
mount: external mount: argv[0] = "/sbin/mount.nfs"
mount: external mount: argv[1] = "10.0.0.101:/opt/Java"
mount: external mount: argv[2] = "/home/viki/Java/virtualServer"
mount: external mount: argv[3] = "-v"
mount: external mount: argv[4] = "-o"
mount: external mount: argv[5] = "rw,noexec,nosuid,nodev,noauto,user,udp"
mount.nfs: timeout set for Wed Oct  6 23:29:27 2010
mount.nfs: text-based options: 'udp,addr=10.0.0.101'
mount.nfs: mount(2): Protocol not supported
mount.nfs: trying 10.0.0.101 prog 100003 vers 3 prot UDP port 2049
mount.nfs: mount to NFS server '10.0.0.101:/opt/Java' failed: RPC Error: Success

---

### Post by luvshines on 2010-10-06
Could this be it ??
[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/537746](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/537746)

It says adding proto=udp solved it for him

You might also want to check if 2049 port is responding from client
nc -zuv <server-ip> 2049

And rpcinfo -p localhost | grep nfs on server side

---

### Post by viki__ on 2010-10-06
It looks that the problem is resolved... an "nfsvers=2" switch in the mount command is the solution. On the NFS server there is Debian, so the nfs versions were most probably not matching.
Thank you very much for the help

---

