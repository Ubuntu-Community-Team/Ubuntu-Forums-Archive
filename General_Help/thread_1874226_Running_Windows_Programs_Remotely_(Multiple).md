---
title: "Running Windows Programs Remotely (Multiple)"
date: 2011-11-02
forum: General Help
---

### Post by computerzoom on 2011-11-02
In Ubuntu Server 11.x how would be the best way to make Windows programs available via remote access through the network? These programs are like MS Access, and Quickbooks Pro (2009 I believe). I need to set up user access level control, make it so certain user group(s) can access these programs through the ubuntu server hopefully more than one remote connection at a time....is this possible and if so how? Using VirtualBox and a SSH X connection perhaps?

Any help would be greatly appreciated,

Thanks In Advance,
Brad

---

### Post by lisati on 2011-11-02
I haven't done it myself, but suspect that it might take a fair bit of work and ingenuity because Windows programs don't run natively on Ubuntu. Ordinarily if you were looking to run them locally, you'd probably need to consider either looking for an Ubuntu-friendly equivalent, or use a program such as Wine that lets you run some (but not all) Windows programs on your Ubuntu box.

---

### Post by computerzoom on 2011-11-02
Thanks, How bout logging into a windows like Windows 7 system on the network that is attached to the server? Accessing software in a virtual environment on one Windows machine through another windows machine that is networked together? Would this be a better possibility?

---

