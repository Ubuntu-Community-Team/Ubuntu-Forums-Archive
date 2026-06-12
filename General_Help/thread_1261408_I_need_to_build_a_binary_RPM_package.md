---
title: "I need to build a binary RPM package"
date: 2009-09-08
forum: General Help
---

### Post by bigboy7foru on 2009-09-08
Ok i have gotten this so far but i can't find these files on my computer. I installed it today the newest version.
 
Is there a certian place they are. I believe i need to install them. These are the ones i need to find. Any and all help is welcomed.
 
Building an OpenVPN binary RPM package requires these RPM prerequisites:
[LIST]
[*]**openssl**
[*]**openssl-devel**
[*]**lzo**
[*]**lzo-devel**
[/LIST] 
 
Thanks Aaron

---

### Post by zvacet on 2009-09-08
Ubuntu use deb not rpm packages.You can try to compile it from source.Or you can try to install  ebox.I think second one is better option.

---

### Post by bigboy7foru on 2009-09-09
I'm not really sure how to do that is there a step by step guide?
 
in new to linux
 
im trying to make this system a VPN server type computer
 
i got this info off of the VPN website:
 
**How can I build a binary RPM package for my specific Linux platform?**

Building an OpenVPN binary RPM package requires these RPM prerequisites:
[LIST]
[*]**openssl**
[*]**openssl-devel**
[*]**lzo**
[*]**lzo-devel**
[/LIST]The **openssl** package is almost always installed by default on Linux distributions. The **openssl-devel** package is almost always available on Linux distributions, but is sometimes not installed by default. The **lzo** and **lzo-devel** packages are usually included in more recent Linux distributions but must be installed manually. See the [[COLOR=#cc6600]Dag Wieers[/COLOR]]("http://dag.wieers.com/packages/lzo/") site for a comprehensive set of LZO RPMs for Red Hat and Fedora.
Once the prerequisite binary RPMs are in place, building an OpenVPN binary RPM is quite straightforward:
[INDENT]**rpmbuild -tb [OpenVPN .tar.gz file] **[/INDENT]You will see a lot of lines of output as **rpmbuild** compiles OpenVPN, but check near the end of the output for a line which looks like this:
[INDENT]Wrote: /usr/src/packages/RPMS/i586/openvpn-2.0_rc18-1.i586.rpm[/INDENT]This tells you where **rpmbuild** wrote the binary RPM file. Now, use:
[INDENT]**rpm -ivh [OpenVPN .rpm file] **[/INDENT]to do a fresh install of OpenVPN, or
[INDENT]**rpm -Uvh [OpenVPN .rpm file] **[/INDENT]to upgrade an existing installation.
 
 
 
Is this correct or is it all wrong?

---

