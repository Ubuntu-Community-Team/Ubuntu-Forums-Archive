---
title: "Windows Client On Ubuntu Server"
date: 2009-10-05
forum: General Help
---

### Post by RyanS93 on 2009-10-05
I found these directions to create an equivalent to a Windows domain server with AD on Ubuntu, which is what I was looking for ([http://www.howtoforge.com/openldap-samba-domain-controller-ubuntu7.10](http://www.howtoforge.com/openldap-samba-domain-controller-ubuntu7.10)). Basically the layout is several Windows machines on a network all connected to an Ubuntu server. Any user would be able to log in to any computer. And, they would have a folder on the server for their file storage that is "attached" to their account, so when they log in, it is automatically mounted and shows up in My Computer, so they can read and save to it, and will be accessible from any computer. What would I need to do to achieve these results? I'd like to save the cost of setting up a Windows server, but using Ubuntu clients may be too much of a change. This sort of situation would be in a small business or the like. This would ensure that everyone's files are in one place. Also, how would I create resource folders on the server that are only accessible to certain groups of users?

While we're at it, how would I configure an Ubuntu server and clients to have the same functions as described above, but with Ubuntu clients?

Thanks!

---

