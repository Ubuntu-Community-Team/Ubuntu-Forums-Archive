---
title: "problems installing ubuntu via netboot"
date: 2011-07-23
forum: General Help
---

### Post by the_genrl on 2011-07-23
hi friends!  pxe is working fine however having issues while installing.

i have the client booting the ubuntu 10.04 server kernel and the netboot install ramdisk.  at boot, i can see the client successfully access the server's NFS share (so that is working) and the server install walk-through appears.

**problem is** it complains to need access to an ubuntu archive.  this computer does not and will not have internet.

**question is** why cant i just completely install ubuntu on the client computer from the server?  i can do that from a CDROM.  also on the server sits an extracted "official ubuntu server" .iso, therefore, everything to to a base install should be available to make the client self-hosting.

**thoughts include** if i switch the netboot ramdisk with the CD install ramdisk, it asks about being unable to mount CD drive.  OK... so does that mean i need to make a custom ramdisk with NFS utilities?  (to enable access the server's NFS share)

i was hoping to make an install just like the CDROM, only without the CDROM and over the network.


thank you for your time

---

### Post by galvatron408 on 2011-07-23
i think you typed something wrong. go back and reread the doc and see where things went wrong.

[https://help.ubuntu.com/community/Installation/LocalNet](https://help.ubuntu.com/community/Installation/LocalNet)

---

### Post by the_genrl on 2011-07-23
hi galvatron408 and thanks for the reply.

you are correct, i am attempting to boot the "ubuntu 10.04 server install" like a "ubuntu 10.04 desktop install".

apparently the process is drastically different from live boot to server installs.  now it looks like my server needs to not only host a NFS but webserver as well.  great.

i will try this and let you know how it goes.

thank you

---

