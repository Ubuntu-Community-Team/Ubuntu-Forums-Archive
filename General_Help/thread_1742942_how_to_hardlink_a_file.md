---
title: "how to hardlink a file"
date: 2011-04-29
forum: General Help
---

### Post by mahmoodn on 2011-04-29
Hi,
I have three nodes with
node1 192.168.1.1
node2 192.168.1.2
node3 192.168.1.3
and the node1 is the head. Problem is when I a new user comes in, I have to create that user on the same machines separately. It is possible to hardlink /etc/passwd and /etc/groups among them. So only one user will be created on the head node. How can I do that?

---

### Post by wizard10000 on 2011-04-29
> **mahmoodn said:**
> Hi,
I have three nodes with
node1 192.168.1.1
node2 192.168.1.2
node3 192.168.1.3
and the node1 is the head. Problem is when I a new user comes in, I have to create that user on the same machines separately. It is possible to hardlink /etc/passwd and /etc/groups among them. So only one user will be created on the head node. How can I do that?

The *right* way to do it is with LDAP or NIS.  You could probably rsync /etc/passwd, /etc/shadow, /etc/group and /etc/gshadow but then you'd probably want to create all your users on node1.  The down side is a simple rsync won't create a home directory on node2 or 3 for the users you've created on node1.

Hope this helps -

---

### Post by mahmoodn on 2011-04-29
Thanks for your tip however I have shared /home among them via NFS. So I think one /home/user directory that is created by node1 is enough.

---

### Post by davrosuk on 2011-04-29
Check out '389 Directory Server' for LDAP and consider using kerberos.

---

### Post by mahmoodn on 2011-04-29
Do you have a link for that? seems that it is working for fedora

---

### Post by davrosuk on 2011-04-29
[http://directory.fedoraproject.org/]("http://directory.fedoraproject.org/")

It started as a Fedora project but it'll work on Ubuntu too - even if it's a bit more tricky.

---

### Post by mahmoodn on 2011-04-29
I will try that. In the mean time, isn't there any simple method for now?

---

### Post by davrosuk on 2011-04-30
'fraid not. Centralised authentication is actually quite a big deal. If you think about it, its only possible in Windows through Active Directory which is just another implementation of LDAP. The tools are prettier in Windows and a lot easier to set-up and use but its the same thing under the hood.

---

