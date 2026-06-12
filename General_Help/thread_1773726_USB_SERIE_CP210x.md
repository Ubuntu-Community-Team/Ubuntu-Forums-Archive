---
title: "USB SERIE CP210x"
date: 2011-06-02
forum: General Help
---

### Post by 19657 on 2011-06-02
Hi all,
I am using Ubuntu for sometime, but lucky me not dealt with device drivers until now.

So I am doing some java code, and all is fine using some CP2102 devices that just use the Ubuntu driver already compiled in kernel.

Now i am using a CP2104 device, which, according to Silabs, must use driver v3.1 from their website.

Now the problem: using Ubuntu supplied driver, device is recognized but runs tons faster baud than it should.
So I tried to include new silabs driver, but it gives an error first about shutdown on usb enumerator. I removed that entry compiled and it seemed fine. Than it generated rpm file, so then I converted to deb, then trying to install some issues because kernel has already CP210x.ko so I "forced" and renamed kernel one and placed mine, of course crash.
So I am desperate now to get some kind of help for this.

Thx

---

