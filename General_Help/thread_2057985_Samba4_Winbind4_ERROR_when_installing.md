---
title: "Samba4 Winbind4 ERROR when installing"
date: 2012-09-14
forum: General Help
---

### Post by enterdavertex on 2012-09-14
I got an error when I'm trying to install Samba4 & Winbind4 into my Ubuntu server, actually i need these version because the NTLM_auth program is inside these package. 

[IMG]http://imageshack.us/a/img442/4877/sanstitredpkg.jpg[/IMG]

Thank you !

---

### Post by Roswebnet on 2013-04-21
Hi
Maybe u don&#8217;t need it already.
However look here:
[http://www.matrix44.net/cms/notes/gnulinux/samba-4-ad-domain-with-ubuntu-12-04](http://www.matrix44.net/cms/notes/gnulinux/samba-4-ad-domain-with-ubuntu-12-04)
 
**Step 4**: Install the Samba 4 Packages
[TABLE="align: center"]
[TR]
[TD]1
[/TD]
[TD]apt-get install samba4
[/TD]
[/TR]
[/TABLE]

The installation will throw out an error and apt will set the package to half installed. As the error isn&#8217;t relevant to us, we have to fix the package by manually setting the package to installed.

[LIST=1]
[*]Edit /var/lib/dpkg/status and search for &#8220;Package: samba4&#8243;
[/LIST]
Replace &#8220;half-configured&#8221; with &#8220;installed&#8221;
 
I think it should resolve your problem.
However, I have problems with using Samba4+Winbind4.
Regards.

---

