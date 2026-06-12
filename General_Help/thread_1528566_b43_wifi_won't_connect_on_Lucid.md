---
title: "b43 wifi won't connect on Lucid"
date: 2010-07-10
forum: General Help
---

### Post by ubun_two on 2010-07-10
I have an old laptop that has bcm4306 (rev 3).  I have used it to install several iterations of Ubuntu in past year or so, and the wifi worked just fine for Intrepid and Kermic, using b43-fwcutter.

However, when I installed Lucid from scratch, I can't get the wife to work.

It says it was installed properly, but I can't see any network around.

Anyone has any idea how I could maybe fix this?

---

### Post by diablo75 on 2010-07-10
You might check this out:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

From the looks of it, your chipset *should* work.  You may need to install b43-fwcutter manually. 

Alternatively you could use Windows drivers with ndiswrapper... which may require you to blacklist the open-source drivers that are included with Ubuntu by default.

Also, often times I do a fresh install on a system that has a wireless adapter but doesn't work right out of the box, about 3/4 of the time is fixed by downloading all the latest system updates from a physical connection and rebooting.  New kernel updates often add better hardware support.

---

### Post by ubun_two on 2010-07-11
Thanks for reply.

I did indeed update everything through wired connection.  I tried uninstalling and reinstalling fwcutter several times.  It just refuses to connect!

I guess I may have to try ndiswrapper ... I thought I'd never have to do that again!

---

