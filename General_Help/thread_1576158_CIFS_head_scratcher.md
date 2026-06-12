---
title: "CIFS head scratcher"
date: 2010-09-16
forum: General Help
---

### Post by Enigmatic on 2010-09-16
I'm at a loss trying to figure this out. If I have my share (hosted on a Debian server) mounted via fstab (nothing fancy, just my credentials and username), using either smbfs or cifs, I obtain speeds of about 37MB/s down, and 15MB/s upload. HOWEVER, if I simply use the "connect to server" option and connect to the share that way, I get a huge increase, with speeds of around 50MB/s both ways! I especially need the upload speed to be increased, as 15MB/s is a painful slowdown for large files.

What could possibly be causing this huge slowdown? They should both be going out via cifs/smbfs, but what is the difference between the two methods? The network/server is more than capable, as I can get 80-100MB/s via FTP.

---

### Post by blueridgedog on 2010-09-16
Try some options in your CIFS mount:

[http://www.samba.org/samba/docs/man/manpages-3/mount.cifs.8.html](http://www.samba.org/samba/docs/man/manpages-3/mount.cifs.8.html)

Start with the directio flag, then take a look at rsize and wsize.

---

### Post by Enigmatic on 2010-09-16
I tried directio as well as rsize and wsize, but it made little difference. Download fluctuated a bit, but upload is still firmly at 15MB/s

---

