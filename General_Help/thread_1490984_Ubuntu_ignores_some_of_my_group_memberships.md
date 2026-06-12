---
title: "Ubuntu ignores some of my group memberships"
date: 2010-05-23
forum: General Help
---

### Post by Raimund Eimann on 2010-05-23
Hi,

I'm running an NFS server which also provides authentication via OpenLDAP.

On that box I've configured ~20 groups which appear nicely on my shiny new lucid box:

drwxr-x--- 496 root bbmovie_k 20480 2010-04-13 21:25 movies/

However, being a member of the bbmovie_k group, I can't cd into the above directory:

$ cd movies/
bash: cd: movies/: Permission denied

I am definitely a member of that group:

$ groups |tr " " "\n" |grep bbmovie_k
bbmovie_k

I am a member of other LDAP-provided groups and I can change into "750"-directories belonging to those without any problems. My question is: what is going on here?

The funny thing is that I can enter the directory after

$ sg bbmovie_k
$ cd movies/
raimund@io:/nfs/m01/movies$

The server is openSuSE 11.1. Until last week the client was openSuSE 11.2. This problem appeared after I reinstalled the client with Lucid Lynx (64bit).

Any ideas? Helpful pointers would be greatly appreciated!

Cheers,
Raimund

---

### Post by dcstar on 2010-05-23
> **Raimund Eimann said:**
> 
.........
The server is openSuSE 11.1. Until last week the client was openSuSE 11.2. This problem appeared after I reinstalled the client with Lucid Lynx (64bit).

Any ideas? Helpful pointers would be greatly appreciated!


Groups have a UID associated with them, since you have re-installed and set up that group again the UID may well now be different and something may have the old UID cached.

The other issue may be the length of the group name and the "_" character which may not be legal in one OS.

---

### Post by WHiZZi on 2010-06-23
Kick!

I have exactly the same problem as above, except we didn't upgrade the server (and server is CentOS). 

It only occurs on 2 pc's so far (both Ubuntu 10.04). Funny enough that my PC (same configuration) is working without problems.

The mount which doesn't work:
> 
fs:/home/shared/noc on /home/user1/fs/noc type nfs (rw,umask=0002,sloppy,addr=172.16.0.5)


on the fileserver (fs):
> 
drwxrwx--- 23 root Techniek       4096 Mar  3 12:12 noc
 [root@fs /home/shared]# 


User information according to "id"
> 
uid=10003(user1) gid=10000(company_users) groups=4(adm),6(disk),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),112(netdev),113(lpadmin),115(powerdev),117(admin),126(libvirtd),10000(company_users),10002(Techniek)


> 
~/fs user1@d-user1 $ cd noc
bash: cd: noc: Permission denied
~/fs user1@d-user1 $ sg Techniek
~/fs user1@d-user1 $ cd noc
~/fs/noc user1@d-user1 $ cd ..
~/fs user1@d-user1 $ groups
company_users adm disk dialout cdrom floppy audio dip video plugdev scanner netdev lpadmin powerdev admin libvirtd Techniek



And here's some actions:
> 
~/fs user1@d-user1 $ cd noc
bash: cd: noc: Permission denied
~/fs user1@d-user1 $ sg company_users
~/fs user1@d-user1 $ cd noc
~/fs/noc user1@d-user1 $ cd ..
~/fs user1@d-user1 $ groups
company_users adm disk dialout cdrom floppy audio dip video plugdev scanner netdev lpadmin powerdev admin libvirtd Techniek


It looks like the secondary groups are not used. Is there someway to fix this or where to look for problem?

---

### Post by WHiZZi on 2010-06-23
Because all of the reactions about this... [/sarcasm], I found the solution...

It seems that NFS cannot handle more than 15 secondary groups. It simply ignores the groups after the 15th one. So, the solution (or at least, workaround) is to remove the user from some local groups in /etc/group :)

---

