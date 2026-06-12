---
title: "VirtualBox Windows XP Service Pack 3"
date: 2010-10-18
forum: General Help
---

### Post by abdusamed on 2010-10-18
Virtualbox 3.2.6 [whichever the latest one on ubuntu 10.04.1] doesn't seem to support Windows XP service pack 3 edition. It installs fine but usually freezes on 'Installing Device' in which I have to reset the virtual machien and try again and it works. But after I installed both the windows and the  virtualbox addon, I always, ALWAYS get a message after some use/boots saying 'Windows system files are changed, please insert Windows Installation Disc'

This never use to pop up with XP service pack 1.

Any recommendation other place where I post this problem/bug/error?

---

### Post by musdem on 2010-10-18
I had a similar problem where this would happen, I fixed it by installing service pack 2 first then installing virtualbox addon then upgrading to service pack 3. Maybe it will work with service pack one.

---

### Post by CharlesA on 2010-10-18
Windows XP SP3 works for me on the latest version of virtualbox on Lucid for me.

Then again, I slipstreamed SP3 onto the install media instead of upgrading from sp1 or sp2.

---

### Post by abdusamed on 2010-10-19
Yes, I don't know why haven't I tried that but I'm not currently in the possession of XP SP2. But I do have XP SP1 which I will try to upgrade to XP SP3 and hope it goes well.

I have one more question, when I tried to install the experimental 3D support and run dxdiag after installing, the 3D test buttons are not available, they're greyed out. Is it something wrong or is it normal? The only reason I'm asking for 3D support is because it might be required in autocad 2009+ which the guest XP doesn't seem to detect. Yes, from the setting I have enabled 3D support with 64mb dedicated which I think is enough.

---

### Post by CharlesA on 2010-10-19
Direct3D support is still experimental at best. I have only been able to use programs that require direct draw, not direct3d.

You can download service pack2 and slipstream it if you really want to, then download sp3.

There are instructions on that floating around the net.

---

