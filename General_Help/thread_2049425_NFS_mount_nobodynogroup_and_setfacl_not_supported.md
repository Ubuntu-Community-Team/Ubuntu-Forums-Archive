---
title: "NFS mount nobody/nogroup and setfacl not supported"
date: 2012-08-28
forum: General Help
---

### Post by sinc93 on 2012-08-28
Hello and thank you in advance for any assistance. I very recently built a new Ubuntu 12.04LTS server which is amazing. I'm mounting storage onto this server from an Oracle NFS device and have a couple of problems:
 
1. The shares get mounted as nobody nogroup using:
 
[SIZE=3][FONT=Calibri]sudo mount -o remount,acl serverip:/export/users/sys_prod /home/sys_prod[/FONT][/SIZE]

[SIZE=3][FONT=Calibri]drwxrwxr-x 3 nobody nogroup 3 Aug 28 10:10 sys_prod/[/FONT][/SIZE]

[FONT=Calibri][SIZE=3]2. My setfacl is not working on this mounted home directory and I believe[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]it's because of the first nobody nogroup problem: ( setfacl works fine on[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]local directories on the Ubuntu server but not on nfs mounts: )[/SIZE][/FONT]

sudo setfacl -m u:melh:--- sys_prod
setfacl: sys_prod: Operation not supported
 
I've searched other solutions and tried modifying my idmapd.conf file as follows:
 
[General]
Verbosity = 0
Pipefs-Directory = /run/rpc_pipefs
# set your own domain here, if id differs from FQDN minus hostname
# Domain = localdomain
[Mapping]
Nobody-User = sys_prod
Nobody-Group = sys_prod
[Translation]
Method = nsswitch
 
Unfortunately this didn't help the problem. If you have any ideas or suggestions
I can try, I would really appreciate it. I'm very new to having root admin so thanks for your patience with my questions.

---

### Post by LewisTM on 2012-08-28
You should install nfs4-acls-tools and run the nfs4_setfacl command instead.

It might bring you closer to a solution. Be aware that this tool works great but that NFS ACLs are not retained upon copy/move, unlike disk-based ACLs.

Cheers!

---

### Post by sinc93 on 2012-08-28
Thank you for your suggestion. I installed the tools: sudo apt-get install nfs4-acl-tools.
Now I'm trying to remove the access from a specific user and don't think I have the correct syntax. Getting "No path(s) specified.". I'll keep trying more combinations but have posted what I'm doing below: If you could please review that would be great. Thank you.
 
 
p-sd-app-14-home]$ls -la
total 51
total 51
drwxr-xr-x 11 root root 4096 Aug 28 08:20 ./
drwxr-xr-x 23 root root 4096 Jul 2 15:35 ../
drwxrwxr-x 3 nobody nogroup 3 Aug 28 10:10 sys_prod/
 
[p-sd-app-14-home]$nfs4_getfacl sys_prod
A::OWNER@:rwaDxtTnNcCoy
A:g:GROUP@:rwaDxtTnNcy
A::EVERYONE@:rxtncy
 
[p-sd-app-14-home]$sudo nfs4_setfacl -m u:melvin:--- sys_prod
No path(s) specified.
 
[p-sd-app-14-home]$sudo nfs4_setfacl -m u:melvin:--- /home/sys_prod
No path(s) specified.

---

### Post by LewisTM on 2012-08-28
The syntax for nfs4_setfacl is very different from setfacl. You will have to familiarize yourself with it by reading the man pages for nfs4_acl and nfs4_setfacl.
For instance the -m switch modifies an existing ACL. Instead you might  enter
```
sudo nfs4_setfacl -a D::melvin@:rwxa sys_prod
```
to _a_dd a new ACL rule _D_enying user melvin _r_ead, _w_rite, e_x_ecute and data _a_ppend rights.

---

### Post by sinc93 on 2012-08-29
Thank you. I will familiarize myself with the nfs4_setfacl syntax and try out more combinations: I did try the following commands but received the following errors:
 
$pwd 
/home
 
$sudo nfs4_setfacl -a D::rahulm@:rwxa sys_prod
Failed setxattr operation: Invalid argument
 
$sudo nfs4_setfacl -a D::rahulm@:rwxa sys_prod/
Failed setxattr operation: Invalid argument
 
$sudo nfs4_setfacl -a D::rahulm@:rwxa /home/sys_prod/
Failed setxattr operation: Invalid argument
 
$sudo nfs4_setfacl -a D::rahulm@:rwxa /home/sys_prod
Failed setxattr operation: Invalid argument
 
$sudo nfs4_setfacl -a D::rahulm@localdomain:rwxa sys_prod
Failed setxattr operation: Invalid argument
 
$sudo nfs4_setfacl -a D::rahulm@localdomain:rwxa /sys_prod
File/directory "/sys_prod" could not be identified
 
$sudo nfs4_setfacl -a D::rahulm@localdomain:rwxa /home/sys_prod
Failed setxattr operation: Invalid argument
 
$sudo nfs4_setfacl -a D::rahulm@localdomain:rwxa /home/sys_prod/
Failed setxattr operation: Invalid argument
 
If you have any more syntax combinations I can try, that would be great!

---

### Post by LewisTM on 2012-08-29
A similar command works here (no error), although not perfectly. It also adds an identical deny rule for the OWNER (??).
You could edit the ACL with your favorite editor to make it look like this:
```
EDITOR=<your editor, default = vi> sudo nfs4_setfacl -e sys_prod
```
> A::OWNER@:rwaDxtTnNcCoy
A:g:GROUP@:rwaDxtTnNcy
A::EVERYONE@:rxtncy
D::rahulm@localdomain:rwaDx
One more comment: I get an Invalid argument error if I try to deny a non-existing user so you should double-check that.

---

### Post by sinc93 on 2012-08-29
Still haven't solved the one problem of removing a single user's access to a specific directory. However did find a good document on the mapping of NFSv4 ACLS vs POSIX ACL's.:
 
[http://www.citi.umich.edu/projects/nfsv4/rfc/draft-ietf-nfsv4-acl-mapping-03.txt](http://www.citi.umich.edu/projects/nfsv4/rfc/draft-ietf-nfsv4-acl-mapping-03.txt)
 
I'm thinking that the mounted Oracle zfs filesystem only supports POSIX ACL's and anything that is not POSIX compliant is being rejected with the setxttr. Any thought's either way? Thanks

---

### Post by sinc93 on 2012-08-29
> **LewisTM said:**
> A similar command works here (no error), although not perfectly. It also adds an identical deny rule for the OWNER (??).
You could edit the ACL with your favorite editor to make it look like this:
```
EDITOR=<your editor, default = vi> sudo nfs4_setfacl -e sys_prod
```
 
One more comment: I get an Invalid argument error if I try to deny a non-existing user so you should double-check that.
 
Thanks I was wondering if perhaps I have the rahulm@localdomain incorrect?
I made sure that I have a correct userid. Since this is a two month old server that I set up, perhaps I need to set the domainname somewhere. 
 
# Checked the user
[p-sd-app-14-var]$cat /etc/passwd | grep rahulm
rahulm:1002:1002:Rahul M,,,:/home/rahulm:/bin/bash
 
I can remove ACL's with the nfs4_editacl and that works ( removed everyone and
it took. ). I'm just thinking it doesn't like that user. The user "rahulm" does not exist on the NFS/ZFS storage device if that matters, just exists on the Ubuntu server. Thanks again for all the suggestions. I'll keep trying more combinations.

---

### Post by sinc93 on 2012-08-29
I found this article [http://comments.gmane.org/gmane.linux.nfsv4/10689](http://comments.gmane.org/gmane.linux.nfsv4/10689)
which has the quote:
 
By the way, this may not be the problem, but: the username needs to be a
valid nfsv4 user name. That means it needs to be of the form
<user>@<domain>, where <domain> is your idmapping domain, and <user> is
a user known to the server.
 
Do you happen to know how to setup/validate that my user is a NFSv4 user and also what domain I need to use. Currently I don't have a specific domain setup in
/etc/idmapd.conf:
 
# set your own domain here, if id differs from FQDN minus hostname
# Domain = localdomain
 
Thanks a lot.

---

### Post by LewisTM on 2012-08-29
This is where my knowledge ends.
I definitely think the username should exist on the NFS4 server, not just locally. The ACL tools must do some validation at that level and remember they are talking to a server, not to Ubuntu.

---

### Post by sinc93 on 2012-08-29
Thank you for pointing me in the right direction with the nfs4_setfacl command. Once I get a resolution to this I will update this thread. Much appreciated!

---

