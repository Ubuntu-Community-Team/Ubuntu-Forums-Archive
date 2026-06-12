---
title: "Mounting an S3 bucket using Fuse and S3FS"
date: 2011-07-05
forum: General Help
---

### Post by fvm2000 on 2011-07-05
I'm trying to mount an S3 bucket using Fuse and S3FS and I've hit a brick wall.

I keep getting the dreaded **fuse: failed to open /dev/fuse: Permission denied** error when I try to mount my bucket.

I've spent countless hours searching for a solution. I've made sure my user is a member of the fuse group, changed permissions on /dev/fuse and on /etc/fuse.conf and on /usr/bin/fusermount. I've rebooted my server several times, you name it, I've done it.

My server is a vps ubuntu 11.04 natty (2.6.18-238.12.1.e15.028stab091.1). I had my ISP (A2.com) enable Fuse on the common kernel.

Anyone have any clues as to what my issue might be?

I'm at my wit's end here...

---

### Post by Habitual on 2011-07-05
this may enlighten you...
[http://xentek.net/articles/448/installing-fuse-s3fs-and-sshfs-on-ubuntu/](http://xentek.net/articles/448/installing-fuse-s3fs-and-sshfs-on-ubuntu/)

---

### Post by fvm2000 on 2011-07-05
Thanks. Turns out I wasn't nuts. The problem was on A2's end. They fixed it after I pointed them to a thread on their own forums from about a year ago... ;)

---

### Post by Habitual on 2011-07-05
that's funny (I used to work hosting support, but I'm in the cloud now!), but glad it worked out.

---

