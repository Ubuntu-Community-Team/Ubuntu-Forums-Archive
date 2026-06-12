---
title: "Why is tar so slow at writing to a cifs share?"
date: 2012-02-07
forum: General Help
---

### Post by ngagun on 2012-02-07
This is on Ubuntu 10.04.

I can write to my cifs share at 250 mbps with cp.

I can tar over my nfs network at close to gigabit speed.

But when I tar to my cifs share, I am only getting 70 mbps.

Any idea how this can happen?

Here is my mount command from /etc/fstab:

//zzz-address /zzz-mount-location cifs credentials=/root/smb/credentials.mbb,uid=0,gid=0 0 0

And here is the tar command:

tar --listed-incremental zzz.snar -cpPf zzz.tar

Any help would be greatly appreciated! Thanks.

---

