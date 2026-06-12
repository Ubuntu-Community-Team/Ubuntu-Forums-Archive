---
title: "ubuntu, esxi and a nfs share."
date: 2010-11-01
forum: General Help
---

### Post by penguin-power on 2010-11-01
Hi everyone!  :D

I have spent many nights here on this forum working through problems with nfs, esxi and backups related to esxi. I want to give something back. At least, make a small and simple howto to maybe help you guys!

Im not an expert, more an explorer....   ;)

--------------------------------------------------------------------

problem:
my business uses 4 esxi servers to run our infrastructure (windoze, ubuntu, centos and bsd).
a.) i need a automatic, intelligent and reliable backup server. (i chose backuppc (in the repos))
b.) i need a fast way to backup whole vm’s. (simple nfs server, to add as a datastore in esxi)

- like many others i have discovered copying a whole 400gb vm is not funny nor easy. moving / copying vm through veeam-fastscp or winscp  is too slow, even with blowfish. 

so i decided to create a nfs share that i could use as a second datastore on all the esxi hosts. I use it like a nas. very fast in comparison to the above mentioned alternative.

i got 2x 1gb hdd’s (used raid1) and installed ubuntu-server 10.04 with backuppc. this is to backup all my data. i also got a 2tb hdd i will use to backup full vm’s. i will mount this 2tb in a share on the backuppc. now, when i copy from the esxi to the nfs-share on ubuntu pc, i get around 50mb/s. in simple terms, 40seconds copy 2gb from/to the simple 2tb nas drive!

so, following are sections: 1.) install and quick config backuppc 2.) quick and dirty nas setup
(copy/paste the yellow code below directly into terminal, changing the relevant bits.)

***********************************************************************************************
*this is a quick and dirty guide - i asume you have a linux and windows client to back up.
* after you tested it all works, its your responsibility to sort out permissions. (this tutorial creates a rw/ro access on the nas share. change it afterwards relevant to your environment.)
------------------------------------------------------------------------------------------------------------------
help and reference:
i got this short howto together with the help of these two sites (...and others.)
...many thanks to them, im just trying to simplify the process. :D
[http://www.howtoforge.com/linux_backuppc](http://www.howtoforge.com/linux_backuppc)
and
ref: [http://blog.roblevine.co.uk/?p=41](http://blog.roblevine.co.uk/?p=41)
-------------------------------------------------------------------------------------------------------------------

1.) backuppc:

on ubuntu server (backuppc)
    code =      yellow background             

sudo passwd root
enable root on ubuntu 

below, edit the files with vim in terminal. or on windows, use putty or winscp to edit them in a gui
edit this file:  /etc/network/interfaces 
(set your: ip/netmask/broadcast/gateway -dont like the terminal? use winscp or gftp)

edit your: /etc/resolv.conf 
(add your search domains or nameservers -usually your dns server or gateway ip)

then: sudo /etc/init.d/networking restart
(restarts with new settings - ssh will kick you off if ip changed. just reconnect.)
---------------------------------------------------
backuppc install on ubuntu server: 

apt-get -y install backuppc htop bmon iotop
installs backuppc, htop, bmon (bandwith monitor) and iotop (like ‘top’, but for hdd’s)

htpasswd /etc/backuppc/htpasswd backuppc
change password for ssh and web for user: “backuppc”

/etc/init.d/backuppc restart
(restart with new settings)
----------------------------------------------------------------------
log into the client pc as root, then run:
ssh-keygen -t rsa
(press enter a few times till done - accept all default options)
(it creates keys and the “.ssh” folder)
----------------------------------------------------------------------

and then on server (backuppc)
logged in as root, run:
su backuppc
(become backuppc)   **not root! - important**

ssh-keygen -t rsa
(press enter a few times, accept all defaults)

cp ~/.ssh/id_rsa.pub ~/.ssh/BackupPC_id_rsa.pub
(copy and paste the above exactly, it creates your new .pub file)

scp ~/.ssh/BackupPC_id_rsa.pub [email]root@xxx.xxx.xxx.xxx:/root/.ssh[/email]/
(secure copy) (your .pub) to (root@client’s .ssh folder) ** replace xxx.xxx.xxx.xxx
-it copies youor .pub file to client’s “root /.ssh” folder
----------------------------------------------------------------------
back on the linux client:
logon as root, then:
cat ~/.ssh/BackupPC_id_rsa.pub >> ~/.ssh/authorized_keys2
(appends your “finger-print” to authorized_keys2)
----------------------------------------------------------------------
back on server (backuppc):
now test your password-less-logon:
ssh -l root xxx.xxx.xxx.xxx
** replace  xxx.xxx.xxx.xxx  with clients ip.
----------------------------------------------------------------------
u r done! now logon to backuppc’s web interface:
[http://xxx.xxx.xxx.xxx/backuppc](http://xxx.xxx.xxx.xxx/backuppc)
------------------------------------------------------------------------

windows clients.
use a local admin account, or like me, a domain user with admin access.
the username for the windows-domain in the config of backuppc i entered like this:
username: domain\username
password: password-here
-------------------------------------------------------------------------

2.) nfs share
on backuppc, make folder in the root: “share”
set permissions to full rw/ro. (folder permissions: 0777)
- remember to comes back and tighten security after you verified it works.
* Add the extra hdd (if needed)

   (login as root)
"fdisk -l" to list disks. (In my case sdb is my 2nd 2tb hdd)

then:
"mount /dev/sdb1 /share".

- this mounts sdb1 (2tb hdd,partition1), into the /share folder.
- again, make sure of permissions to "0777" on "/share"
Installing NFS and exporting your share

Install your NFS server:
apt-get -y install portmap nfs-kernel-server

Export your shared directory by editing "/etc/exports" and adding the ip address of esxi:
/share xxx.xxx.xxx.xxx(rw,async,no_subtree_check) - replace x’s with the esxi ip

run:
exportfs -ra

start / restart the NFS service:
/etc/init.d/nfs-kernel-server restart

You should now have an exported NFS share!
Mounting your NFS share from ESXi

Start up the VMWare Infrastructure client and log into your ESXi server
Select Configuration->Storage and choose "Add Storage"
Choose "Network File System"
For the "server", enter the IP address of your Ubuntu server
For the "folder", enter the full path to the exported folder: "/share"
For the "datastore name", enter a meaningful name, e.g. "nfs-backuppc"
You should now be able to see the remote NFS share from the ESXi host.

Backing up your VM once a month

right-click datastore -> browse local datastore.
right-click the folder and select “copy”.
close datastore
right-click datastore "nfs-backuppc" -> browse datastore
right-click on the rightside in datastore and “paste” 
on a gb switch, you will see between 40-60mb/s. (1gb/20seconds)


example exports file:
# ........................................................................................................................
# /etc/exports: the access control list for filesystems which may be exported
#  to NFS clients.  See exports(5).
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#
# esxi 1 ip
/share xxx.xxx.xxx.xxx(rw,async,no_subtree_check)
#
# esxi 2 ip
/share xxx.xxx.xxx.xxx(rw,async,no_subtree_check)
# ........................................................................................................................

Note: After a reboot:

log in as root, then:

1. mount 2tb
mount /dev/sdb1 /share

2. export share / folders
sudo exportfs -ra

3. restart service
/etc/init.d/nfs-kernel-server restart

....then you have nfs-again

---

