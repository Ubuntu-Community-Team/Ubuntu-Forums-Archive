---
title: "simple way to trigger root-level process?"
date: 2010-06-29
forum: General Help
---

### Post by bloer on 2010-06-29
Hi all,

I have what I hope someone finds to be a simple problem.  I am running a data acquisition computer for a research project, where multiple people use the same non-privileged user account to take data and save it to /incoming.  Once the file has been closed, I would like to somehow copy the data into a more permanent location owned by root.  Obviously giving the shared user account sudo permission would be a huge security hole.

I know that this should be possible using some sort of client/server connection, but writing my own server just for this little task seems a bit cumbersome, and is something I have no experience with.  Nor have I ever written a daemon/init script before.

Does anyone have any ideas on a simple procedure I could use?  Very few things are fixed in stone, but the copy operation is necessary - the final location is a RAID5 array, and the write speeds are too slow to keep up with the data stream.  

If a client/server type of thing really is the best way to go, anyone have any links to good tutorials to make a simple server and daemonize it?

Thanks!

---

### Post by bodhi.zazen on 2010-06-29
> **bloer said:**
> Hi all,

I have what I hope someone finds to be a simple problem.  I am running a data acquisition computer for a research project, where multiple people use the same non-privileged user account to take data and save it to /incoming.  Once the file has been closed, I would like to somehow copy the data into a more permanent location owned by root.  Obviously giving the shared user account sudo permission would be a huge security hole.

I know that this should be possible using some sort of client/server connection, but writing my own server just for this little task seems a bit cumbersome, and is something I have no experience with.  Nor have I ever written a daemon/init script before.

Does anyone have any ideas on a simple procedure I could use?  Very few things are fixed in stone, but the copy operation is necessary - the final location is a RAID5 array, and the write speeds are too slow to keep up with the data stream.  

If a client/server type of thing really is the best way to go, anyone have any links to good tutorials to make a simple server and daemonize it?

Thanks!

This is a perfect scenario for sudo.

su - is all or none, but sudo allow you to define which processes one can run as root.

See: [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

[https://help.ubuntu.com/community/Sudoers#User%20Specifications](https://help.ubuntu.com/community/Sudoers#User%20Specifications)

[http://www.sudo.ws/sudo/sudoers.man.html](http://www.sudo.ws/sudo/sudoers.man.html)

---

### Post by bloer on 2010-06-30
> **bodhi.zazen said:**
> This is a perfect scenario for sudo.
[]("http://www.sudo.ws/sudo/sudoers.man.html")

Thanks for the quick and direct answer!  I had forgotten that sudo can be restricted to only allow certain commands.

---

