---
title: "Guide to make PXE image"
date: 2010-01-27
forum: General Help
---

### Post by bakegoodz on 2010-01-27
I can find plenty of Guide to make custom CD. Is there any to make a PXE image from a working install? Or even PXE from a CD image is fine, since I want to make both from a console only install of Ubuntu.
Thanks

---

### Post by t4thfavor on 2010-01-27
Lots of tutorials on PXE booting, One that deals with ubuntu a little is here.

[http://www.howtoforge.com/ubuntu_pxe_install_server](http://www.howtoforge.com/ubuntu_pxe_install_server)

It's really pretty much the same for all linux's you send down the kernel, and then tell it where the rootfs is, and then your up and running.

---

### Post by bakegoodz on 2010-01-28
Yes I understand how to setup a PXE server. Thanks for your effort, but that wasn't what I was asking. I need guidance in setting the remote boot files for a PXE server. In my mind there must be a fairly simple way to extract and modify a few files from a Live CD for remote booting. I think I understand most the concepts, but having some of the steps laid out would help get me all the way to my goal.

---

### Post by lykwydchykyn on 2010-01-28
You mean like this:
[https://wiki.ubuntu.com/LiveCDNetboot](https://wiki.ubuntu.com/LiveCDNetboot)

I have this working with several different Live CDs.  Every distro is a bit different, but the *buntus are all the same.

Only problem I had is that certain network cards didn't have drivers in the initrd and couldn't connect back to the NFS share to mount the disc files.  Barring that, it works great.

---

### Post by bakegoodz on 2010-01-28
Thanks!

---

