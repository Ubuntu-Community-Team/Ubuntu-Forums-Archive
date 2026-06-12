---
title: "NFS advice - Web server and remote user"
date: 2010-03-07
forum: General Help
---

### Post by Lilltjalle on 2010-03-07
Hi
Here's a situation that I do not know how to handle, and I am looking for some advice from a security point of view.

Box A, a Ubuntu 8.04 Web server, and box B, a Ubuntu 9.10 client.
From box B, I need to have read/write access to the contents of the /var/www folder on the server, box A.

Now, which would be a suitable solution, that also keep security as intact as possible?

Changing the attributes (owner / permissions) on the /var/www folder does not seem suitable to me, but that's me...
Should the remote user on the client be a member of a group that have permission?

I'm lost and could really use some advice. Thanks.

---

