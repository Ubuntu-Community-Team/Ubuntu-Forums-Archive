---
title: "HA Storage Cluster for Windows?"
date: 2012-05-02
forum: General Help
---

### Post by sureshot007 on 2012-05-02
So I've spent the last couple days on google, reading as much information as my brain can handle, and I think it's finally turned to mush.

Here's what I'm trying to accomplish: HA storage for Windows profile redirection.  There will probably be room for regular file server type storage there too, but the profile redirection is the important part.

I looked into Gluster, which sounded awesome at first, until I realized that there is no native windows support, so I'd still need to share the volumes out via smb.  Not a deal breaker, but it negates the benefit of the distributed access if all the users have to access it through one node.  Other than that, Gluster is the ideal solution for me (stupid windows....)

So what is the "best practice" for something like this?  2 nodes with heartbeat style failover and fibre channel JBODS?  Is there any way to make Gluster a little more ideal for windows stuff?  Is there another option that I haven't tried yet?

---

