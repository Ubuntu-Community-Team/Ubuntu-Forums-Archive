---
title: "Collaborative network shares without compromising security"
date: 2010-08-27
forum: General Help
---

### Post by panfist on 2010-08-27
I'm in the process of working out a few kinks of setting up Ubuntu services for a small business network. We have successfully used a web server running mediawiki, and some basic NFS services so far. A special type of network share that I need provided by my file server is one in which users are free to read and write each others' files. I'm not sure if NFS is best suited to the task, or if this is something that's more suited to Samba.

The default umask set in /etc/profile of an Ubuntu workstation is 022. This lets users read and write their own files, and allow other users in any group to read their files. This is perfectly fine in most situations; however, we need a shared workspace where users can edit each others' files. I could set the umask to 002, or even 000, but I doubt that's a good practice. This means that on each local system, other users could edit files in each others' home directories. Actually, I'm not even sure if this is true, if the proper permissions are set on users' top-level home directories, but files under those directories would have too-loose permissions set on them.

In general, I want to keep the default umask of 022, but I want a specific share (whether it's NFS, Samba, or something else entirely) to behave like umask 000. I know I could do this in Samba, but my instincts tell me that there is probably a better way.

Could you please share how you provide this service on your networks? What are some good practices to follow? Are there any risks to providing this type of service that aren't immediately apparent?

---

### Post by panfist on 2010-08-28
bump

---

### Post by panfist on 2010-08-30
bump

---

### Post by panfist on 2010-09-10
bump

---

