---
title: "Login Scripts and Mounting Shares"
date: 2012-02-26
forum: General Help
---

### Post by gmjs on 2012-02-26
Hello,

It seems there are many ways to mount a share on user login, but I haven't found the best way to mount a share when the path depends on:

1. the hostname of the client, or
2. group membership of the user

I'd like to mount a Windows samba share based on part of the client hostname, a Windows samba share based on group membership and username, and a Linux NFS share based on username at startup.

Obviously, I need to script part of this.  What's the best way to do it?

Many thanks.

---

