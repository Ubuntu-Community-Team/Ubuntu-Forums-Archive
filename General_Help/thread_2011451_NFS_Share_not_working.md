---
title: "NFS Share not working"
date: 2012-06-27
forum: General Help
---

### Post by DurbanDriver on 2012-06-27
Sorry if I have missed something stupid but I have searched and tried various how to's but I am still unable to share a directory via nfs on 10.04.4.client and server.

I have installed nfs-kernel-server, nfs-commons and portmap on both client and sever.
rpcinfo -p shows all the required ports.
hosts.allow contains ALL: ALL
hosts.deny contains nothing
ufw is disabled

On the client showmount -e serverIP shows the two directories, but 
mount -o nolock serverIP:/images/dev /mnt/test just times out with:
 "mount.nfs: mount system call failed".

I tried the mount on the server and it works.

What am I missing, please, have been pulling my hair out for days.

---

### Post by Azdour on 2012-06-27
Hi,

What do you have in your /etc/exports file?

---

### Post by DurbanDriver on 2012-06-27
> **Azdour said:**
> Hi,

What do you have in your /etc/exports file?

The following:

/images      *(ro,sync,no_wdelay,insecure,no_root_squash,no_subtree_check)
/images/dev  *(rw,sync,no_wdelay,insecure,no_root_squash,no_subtree_check)

Have tried replacing the * with IP subnet (192.168.103.0/24) but it made no difference.
Any help much appreciated.

---

### Post by Azdour on 2012-06-29
Hi,

Sorry for the delay in responding.

Some more things to test:

Does /mnt/test exist?

Once you set up the exports file did you run:

```
sudo exportfs -a
```

Then restart portmap and nfs-kernel-server?

Does missing out the nolock option work?

```
mount -serverIP:/images/dev /mnt/test
```

---

### Post by DurbanDriver on 2012-07-02
> **Azdour said:**
> Hi,

Sorry for the delay in responding.

Some more things to test:

Does /mnt/test exist?

Once you set up the exports file did you run:

```
sudo exportfs -a
```

Then restart portmap and nfs-kernel-server?

Does missing out the nolock option work?

```
mount -serverIP:/images/dev /mnt/test
```

Yes
yes
No difference.

Sorry for the delay. I was away over the weekend.
Any further help much appreciated. I really need to get this working.

---

### Post by SeijiSensei on 2012-07-02
You are using sudo to mount the share, right?

What do you see in /var/log/syslog on the server when the mount fails?

---

### Post by DurbanDriver on 2012-07-02
yes am using sudo.

sudo mount 192.168.103.246:/images/dev /mnt/test
[sudo] password for tim:
mount.nfs: mount system call failed
tim@fog10:~$

No messages in syslog on the client or the server. It's almost like nothing is happening!

---

### Post by Azdour on 2012-07-02
Hi,

Are portmap and nfs-kernel-server actually running. I remember in the past I've had a silent failure.

```

sudo /etc/init.d/portmap status
sudo /etc/init.d/nfs-kernel-server status

```

Both these should return the running process id if running.

Can you ping the server from the machine you want to mount the nfs on?

Slowly running out of ideas why it is not working.

---

### Post by DurbanDriver on 2012-07-02
portmap start/running, process 685
and
nfsd running

Yep the machines can both ping each other, and showmount client shows :

tim@fog10:~$ showmount -a 192.168.103.246
All mount points on 192.168.103.246:
192.168.103.246:/images/dev
tim@fog10:~$ showmount -e 192.168.103.246
Export list for 192.168.103.246:
/images/dev *
/images     *
tim@fog10:~$

Please dont give up yet!

---

### Post by Azdour on 2012-07-03
Hi,

Clutching at straws but could you try simpler options for the mounts, you have:

```

/images *(ro,sync,no_wdelay,insecure,no_root_squash,no_sub tree_check)
/images/dev *(rw,sync,no_wdelay,insecure,no_root_squash,no_sub tree_check)

```

Could you remove the no_wdelay and insecure to see if its one of these options that are causing you the problem. I'm sure it isn't the issue but at least it rules that out.

---

### Post by DurbanDriver on 2012-07-03
OK tried that. No difference. Connection just times out with no message in syslog.

---

### Post by Merrattic on 2012-07-03
Try setting up again, following exactly this straight forward tutorial [http://ubuntuforums.org/showthread.php?t=249889&highlight=NFS](http://ubuntuforums.org/showthread.php?t=249889&highlight=NFS)

This has worked every time for me. Once you have this working, you can edit your settings.

You don't need nfs-kernel-server on the clients, just nfs-common and portmap

---

### Post by SeijiSensei on 2012-07-03
> **DurbanDriver said:**
> No messages in syslog on the client or the server. It's almost like nothing is happening!

No messages in the server's log tells me there is a connectivity problem of some kind.  Try installing nmap from the repositories and do both a TCP and a UDP scan of the server from the client.  (You need to run these as root.)  I realize that showmount suggests there isn't a network problem, but you should see entries in the server's syslog corresponding to the requests.  On my CentOS servers, these messages are attributed to the mountd process in the log.

---

### Post by DurbanDriver on 2012-07-03
Thank you SeijiSensei & Merrattic . Will try those and get back to you shortly.

---

### Post by DurbanDriver on 2012-07-04
> **Merrattic said:**
> Try setting up again, following exactly this straight forward tutorial [http://ubuntuforums.org/showthread.php?t=249889&highlight=NFS](http://ubuntuforums.org/showthread.php?t=249889&highlight=NFS)

This has worked every time for me. Once you have this working, you can edit your settings.

You don't need nfs-kernel-server on the clients, just nfs-common and portmap

I am working through all the messages in that post and trying all the troubleshooting tips. So far no difference. I still get, on the client (192.168.103.107):

tim@fog10:/$ sudo mount 192.168.103.246:/images/dev /files
[sudo] password for tim:
mount.nfs: mount system call failed

yet showmount -e 192.168.103.246 shows the directories are exported and rpcinfo -p 192168.103.246 shows the ports are setup.\Going to try nmap now.

---

### Post by DurbanDriver on 2012-07-04
Output from nmap on the client pointed to the server:
Completed Connect Scan at 12:52, 0.04s elapsed (1000 total ports)
Host fogserver.ehs.local (192.168.103.246) is up (0.0019s latency).
Interesting ports on fogserver.ehs.local (192.168.103.246):
Not shown: 995 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
22/tcp   open  ssh
80/tcp   open  http
111/tcp  open  rpcbind
2049/tcp open  nfs

Read data files from: /usr/share/nmap
Nmap done: 1 IP address (1 host up) scanned in 0.11 seconds

---

### Post by Merrattic on 2012-07-04
Where is "/files" (your mount point on the client) ?? Is this the full path ?

Who "owns" /images and /images/dev ?

Are /images and /images/dev on the same HDD as the OS ? Sometimes you need to mount these with fstab to make everything work?

See if you can get to a point where you have the same named user and UID on both client and server, I have found this helps.

---

### Post by DurbanDriver on 2012-07-04
/files is the full path. I did sudo cd /, sudo mkdir files.

I mages is owned by root:root

yes they are on the same drive as the OS.

There is only one user on each machine, and that is me.

---

### Post by Merrattic on 2012-07-06
Helpful link? [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch29_:_Remote_Disk_Access_with_NFS#Troubleshooting_NFS](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch29_:_Remote_Disk_Access_with_NFS#Troubleshooting_NFS)

---

