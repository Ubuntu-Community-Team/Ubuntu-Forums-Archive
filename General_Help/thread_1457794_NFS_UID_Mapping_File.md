---
title: "NFS UID Mapping File"
date: 2010-04-19
forum: General Help
---

### Post by dragos2 on 2010-04-19
I need some insight regarding the near not documented (can't see it in manual either) but you can read an example here:
[http://www.kernelcrash.com/blog/nfs-uidgid-mapping/2007/09/10/](http://www.kernelcrash.com/blog/nfs-uidgid-mapping/2007/09/10/)

This is supposed to solve the UID mapping between the NFS server and client, I found this in this book: 
[http://books.google.ro/books?id=xVuoTgSL1QoC&lpg=PA218&ots=ZcAjdIa5b1&dq=%2Fhome%20%20larch(rw%2Cmap_static%3D%2Fetc%2Fnfs%2Flarch-map)&pg=PA217#v=onepage&q&f=false](http://books.google.ro/books?id=xVuoTgSL1QoC&lpg=PA218&ots=ZcAjdIa5b1&dq=%2Fhome%20%20larch(rw%2Cmap_static%3D%2Fetc%2Fnfs%2Flarch-map)&pg=PA217#v=onepage&q&f=false)

And in short using this export and the map file should do the job.
[FONT=&quot][/FONT]  [FONT=&quot]/home  larch(rw,map_static=/etc/nfs/larch-map)[/FONT]
  
I did not tested it yet, also it does not states if its a NFS 3 or 4 thing.

I have 3 questions:

1) Is this present in Ubuntu ?
2) How do I map a user with many gid's ?
3) Why in the world there is no documentation about this ?

---

### Post by ilium007 on 2010-05-25
I would like an answer on this as well. When I try to use map_static in my exports file I get this:
exportfs: /etc/exports:1: unknown keyword "map_static=xxxxxxxx

---

### Post by srs5694 on 2010-05-25
I'm the author of the book you referenced. Unfortunately, that documentation is rather old (the book has a 2002 copyright date). It's been a while since I looked into this in detail, but I believe the map_static option is no longer supported. If there's a direct and simple replacement, I don't know what it is.

Many installations now employ LDAP ([https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)) to manage users across multiple systems. This keeps their UIDs identical so there's no need for NFS UID mapping. Unfortunately, although LDAP is a great tool for big sites, it's complex enough that keeping it running and properly configured is a big challenge for a small site such as a home network.

Another option might be to use Samba rather than NFS. Samba handles permissions differently than NFS. It's been a while since I looked into it in any depth, so I'm not sure if it would really be any better -- it might have its own set of problems for your specific setup, or it might fix things in its default configuration.

---

### Post by dragos2 on 2010-05-26
> **srs5694 said:**
> I'm the author of the book you referenced. Unfortunately, that documentation is rather old (the book has a 2002 copyright date). It's been a while since I looked into this in detail, but I believe the map_static option is no longer supported. If there's a direct and simple replacement, I don't know what it is.

Many installations now employ LDAP ([https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)) to manage users across multiple systems. This keeps their UIDs identical so there's no need for NFS UID mapping. Unfortunately, although LDAP is a great tool for big sites, it's complex enough that keeping it running and properly configured is a big challenge for a small site such as a home network.

Another option might be to use Samba rather than NFS. Samba handles permissions differently than NFS. It's been a while since I looked into it in any depth, so I'm not sure if it would really be any better -- it might have its own set of problems for your specific setup, or it might fix things in its default configuration.

Hi, great to know you and thanks for stopping by and taking time to answer.

Yes, LDAP can be a good candidate here but I was looking for a way to mount a share that uses ACL and NFS v3 is the only client that can do this properly. NFS v4 uses non POSIX ACLs unfortunately.

Samba shares can be mounted remotely with proper ACL permissions only by using Gnomes built in .gvfs filesystem and only in recent versions of Gnome this works decent enough to support ACL's and not crash so often.

We ended up using NFS v3 with uid and gid synchronization. The second solution that does not involves synchronization is Gnome's gvfs and it can mounts samba and nfs shares I guess but never looked into detail.

---

