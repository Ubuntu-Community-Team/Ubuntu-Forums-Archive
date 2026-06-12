---
title: "Cant mount NTFS drive via NFS in natty"
date: 2011-05-27
forum: General Help
---

### Post by quint6 on 2011-05-27
Well, yesterday i decided to try out NFS, which absolutely went beyond expectation for speed and reliability. Just today i decided i would upgrade to natty, then i tried to mount a directory thats on the NTFS drive via NFS over my network and all of a sudden it just refuses to work.

(i have sudo'd using the correct password)

i am now prompted with:

user@acer:~$ sudo mount 192.168.0.2:/media/Secondary/Media/Movies /test
[sudo] password for user: 
mount.nfs: access denied by server while mounting 192.168.0.2:/media/Secondary/Media/Movies

this is my exports file:
# /etc/exports: the access control list for filesystems which may be exported
#        to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#

/media/Secondary/Media/Movies    *(ro)

this will work if i choose rw, but i want ro

---

### Post by wildmanne39 on 2011-05-27
> **quint6 said:**
> Well, yesterday i decided to try out NFS, which absolutely went beyond expectation for speed and reliability. Just today i decided i would upgrade to natty, then i tried to mount a directory thats on the NTFS drive via NFS over my network and all of a sudden it just refuses to work.

i am now prompted with:

user@acer:~$ sudo mount 192.168.0.2:/media/Secondary/Media/Movies /test
[sudo] password for user: 
mount.nfs: access denied by server while mounting 192.168.0.2:/media/Secondary/Media/Movies

this is my exports file:
# /etc/exports: the access control list for filesystems which may be exported
#        to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#

/media/Secondary/Media/Movies    *(ro)
Hi, when it asks for password did you enter your user password that you set up when you installed ubuntu?

---

### Post by quint6 on 2011-05-28
> **wildmanne39 said:**
> Hi, when it asks for password did you enter your user password that you set up when you installed ubuntu?

I've never had to enter a password while mounting an NFS share. I can do this properly with a directory thats on my ext4 filesystem but as soon as i implement a directory that is on my NTFS drive, then access denied is returned. This only started happening when i upgraded to natty, the other day i was using it error free.

I am confident that I'm configuring /etc/exports properly, unless in natty on NFS i have to define that it is an NTFS drive.

---

### Post by wildmanne39 on 2011-05-28
> **quint6 said:**
> I've never had to enter a password while mounting an NFS share. I can do this properly with a directory thats on my ext4 filesystem but as soon as i implement a directory that is on my NTFS drive, then access denied is returned. This only started happening when i upgraded to natty, the other day i was using it error free.

I am confident that I'm configuring /etc/exports properly, unless in natty on NFS i have to define that it is an NTFS drive.
Hi, I understand that you did not have to in the past and I do not know why it is asking now, but enter you password and see if it works.I wish I could be of more help maybe someone will post what you need to fix the problem.

---

### Post by quint6 on 2011-05-29
bumpity bump

---

### Post by billschu on 2011-08-09
same issue moving some machines from 10.04 to 11.04 but only 11.04 client trying to mount to 9.10 server - 10.04 clients mount to 9.1 server fine, 9.1 client mounts to 11.04 or 10.04 servers fine

all nfs3 shares

obviously my solution would be to upgrade the 9.1 server but not ready to do all that entails in my case

update - with no changes to any /etc/exports after a day (including reboots of all machines involved) now everything is mounting as it should.

---

