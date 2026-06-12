---
title: "fakeroot and sudo"
date: 2010-09-10
forum: General Help
---

### Post by blue_penguin on 2010-09-10
is fakeroot the same as sudo? 
fakeroot - remove the need to become root for a package build
sudo - root privilileges

mainly, how do they differ?

---

### Post by TwelveGauge on 2010-09-10
just use sudo.
I've seen fakeroot cause problems and using sudo is the 'proper' way to go about package building. What fake root does is change ownership of files to root:root instead of user:user. It's meant for installing packages on your user account, but if you want to install to system directories you MUST use sudo or be root.

---

### Post by Grenage on 2010-09-10
As far as I understand it:

Fakeroot: creates the illusion of root privileges in a kind of 'wrapper'.  Never does it have any real privileges.

Sudo: temporary escalation of privileges to that of root.  Real privileges and system access.

---

### Post by blue_penguin on 2010-09-10
so when i use 
   *[FONT=&quot]fakeroot make-kpkg --initrd –-append-to-version=-kernel7 kernel_image kernel_headers[/FONT]*
is it the same as
   *[FONT=&quot]sudo make-kpkg --initrd –-append-to-version=-kernel7 kernel_image kernel_headers[/FONT]*

---

### Post by TwelveGauge on 2010-09-10
no, not quite. 

Fakeroot has only one--and it's a partial one at that--application and that's to get around the need for sudo access. It's not the same. What it was meant to do was provide people (without sudo access) to install stuff on their user account. If you can use sudo, use it. Fakeroot is **not** the same as **sudo**. 

Basically, it comes down to this: 
"Why do you want to use fakeroot over sudo anyway?" 

Sudo is better, it is the proper way. Use it.

---

