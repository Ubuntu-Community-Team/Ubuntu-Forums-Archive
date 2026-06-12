---
title: "Wireshark"
date: 2011-05-10
forum: General Help
---

### Post by jhall1990 on 2011-05-10
Hello,

This is not a Ubuntu issue per say but I figured I would ask anyway. I am currently running Ubuntu 11.04 and I am having trouble with wireshark. The program itself is running fine but I really do not like the newest version and much prefer the version I had when I was running 10.10. Is there anyway that I can roll back to the version that is used in 10.10?

Thanks in advance.

---

### Post by jhall1990 on 2011-05-10
Can anyone help me with this?

---

### Post by Dave_L on 2011-05-10
All the versions are available here:

[http://packages.ubuntu.com/search?keywords=wireshark&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=wireshark&searchon=names&suite=all&section=all)

I would examine the dependencies before trying to downgrade, since other packages could be affected.

---

### Post by uRock on 2011-05-10
> **jhall1990 said:**
> Can anyone help me with this?

Please wait 24 hours before bumping your thread.

---

### Post by jhall1990 on 2011-05-10
> **Dave_L said:**
> All the versions are available here:

[http://packages.ubuntu.com/search?keywords=wireshark&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=wireshark&searchon=names&suite=all&section=all)

I would examine the dependencies before trying to downgrade, since other packages could be affected.

How do I download the package from that site?

---

### Post by pqwoerituytrueiwoq on 2011-05-10
open synaptic package manager -> find package -> press [Crtl]+[E]
pretty obvious from there
if you cant find the version you want you may want to add a ppa or find some deb files

---

### Post by jhall1990 on 2011-05-12
When I hit control E nothing happens. When I check the properties of the package the only available version is the one that I have. Is there any website you can recommend where I might be able to find this?

---

### Post by Dave_L on 2011-05-13
> **jhall1990 said:**
> How do I download the package from [that site](http://packages.ubuntu.com/search?keywords=wireshark&searchon=names&suite=all&section=all)?

Example:

Under "Package wireshark", there's a list of Ubuntu versions. Click on the link "maverick".

That takes you to a page with "Package: wireshark (1.2.11-6+squeeze1build0.10.10.1)" at the top. At the bottom of that page are links "amd64" and "i386".  Click on one of those links to download a .deb. 

-----

But I'm not sufficiently knowledgeable to tell you the best way to downgrade.  Maybe uninstalling your current version of wireshark, and then installing the downloaded .deb will work.  Or maybe that will cause problems, possibly messing up your system.

---

