---
title: "Oracle 11g express database rpm"
date: 2012-08-10
forum: General Help
---

### Post by p3aul on 2012-08-10
Oracle only offers this database in rpm format(seems like they only love RedHat) Every bit of info I get says "Just use Alien" Well I have it and I am pulling my hair out trying to convert it to a deb! Every website says do this as root: 
```
#Alien filename.rpm
```and the deb is created. Not so! I get an "Unknown tag error" I tried to use the -d tag even though I'm not supposed to need it, but still; no go.

Has some one already created a deb for this file and could give me a link to it? I would be so grateful!
Thanks,
Paul

---

### Post by Cheesemill on 2012-08-11
Sometimes alien just doesn't work, which isn't surprising considering what it is trying to do.

Can you downloaded the source code and compile that instead?

---

### Post by p3aul on 2012-08-11
thats so involved and complicated there may be dozens of file to try to figure out which one to begin with. Surely someone has created a deb of this software and be willing to share it. :(

---

### Post by lykwydchykyn on 2012-08-11
Can you post the full command that you're running and the complete output?

---

### Post by Habitual on 2012-08-12
Operating system
   [One of the following:]("http://docs.oracle.com/cd/E17781_01/install.112/e18802/toc.htm#BABGGAJA")
 
[LIST]
[*] Oracle Enterprise Linux 4 Update 7
[*] Oracle Enterprise Linux 5 Update 2
[*] Red Hat Enterprise Linux 4 Update 7
[*] Red Hat Enterprise Linux 5 Update 2
[*] SUSE Linux Enterprise Server 10 SP2
[*] SUSE Linux Enterprise Server 11
[/LIST]
NOTE: CentOS is perfect for Oracle. :)

---

