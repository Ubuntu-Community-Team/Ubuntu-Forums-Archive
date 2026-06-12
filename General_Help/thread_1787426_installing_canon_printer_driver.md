---
title: "installing canon printer driver"
date: 2011-06-21
forum: General Help
---

### Post by tp21 on 2011-06-21
hi,
i am running T43 Thinkpad box with Ubuntu 11.04. 
we have a canon network printer model i-SENSYS MF4570dn printer, and i am trying to install the UFR II driver which i downloaded from canon website. the problem i am facing is that when i install the driver with gdebi i receive error message saying: Dependency is not satisfiable: gs-esp.
i tried to install ge-eps but it is not part of the repository for 11.04 :(
any ideas?
thanks in advance

---

### Post by nomko on 2011-06-21
[https://launchpad.net/ubuntu/+source/gs-esp/8.15.2.dfsg.0ubuntu1-0ubuntu1.2](https://launchpad.net/ubuntu/+source/gs-esp/8.15.2.dfsg.0ubuntu1-0ubuntu1.2)
 
It looks like it was ment for Ubuntu 6.06 LTS Dapper Drake... Don't know if it's gonna work for 11.04.
 
*edit*
Looks like you're lucky: [http://www.ubuntuupdates.org/packages/show/274517](http://www.ubuntuupdates.org/packages/show/274517)

---

### Post by tp21 on 2011-06-21
thanks a lot.
but the link leads to ghostscript package, and i allready have this one. 
as far as i can see there is no package called gs-esp for natty. :(

---

### Post by nomko on 2011-06-21
Okay, try these links:
 
[https://launchpad.net/ubuntu/natty/+package/gs-esp](https://launchpad.net/ubuntu/natty/+package/gs-esp)
 
[https://launchpad.net/ubuntu/natty/i386/gs-esp-x](https://launchpad.net/ubuntu/natty/i386/gs-esp-x) (32-bit CPU)
 
[https://launchpad.net/ubuntu/natty/amd64/gs-esp](https://launchpad.net/ubuntu/natty/amd64/gs-esp) (64-bit CPU)
 
Just found a topic on this forum:
[http://ubuntuforums.org/archive/index.php/t-1710037.html](http://ubuntuforums.org/archive/index.php/t-1710037.html)

---

### Post by tp21 on 2011-06-21
thanks again
the link on ubuntu forum was helpful, i installed the security package as it is described there, but i had no luck with installing the printer driver. i can not really understand why the driver depends on a package which is no longer there.

---

### Post by tp21 on 2011-06-21
oh, i was too fast. it did work :))))
first i installed the security package under:
[http://security.ubuntu.com/ubuntu/pool/universe/c/cups/cupsys_1.4.3-1ubuntu1.3_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/c/cups/cupsys_1.4.3-1ubuntu1.3_all.deb)
then i installed the gs-eps package under this link you mentioned:
[https://launchpad.net/ubuntu/natty/i386/gs-esp/8.71.dfsg.2-0ubuntu7](https://launchpad.net/ubuntu/natty/i386/gs-esp/8.71.dfsg.2-0ubuntu7)
then i installed canon driver. and my first page came out of the printer.
thaks a million

---

### Post by nomko on 2011-06-21
------

---

### Post by nomko on 2011-06-21
> **tp21 said:**
> oh, i was too fast. it did work :))))
first i installed the security package under:
[http://security.ubuntu.com/ubuntu/pool/universe/c/cups/cupsys_1.4.3-1ubuntu1.3_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/c/cups/cupsys_1.4.3-1ubuntu1.3_all.deb)
then i installed the gs-eps package under this link you mentioned:
[https://launchpad.net/ubuntu/natty/i386/gs-esp/8.71.dfsg.2-0ubuntu7](https://launchpad.net/ubuntu/natty/i386/gs-esp/8.71.dfsg.2-0ubuntu7)
then i installed canon driver. and my first page came out of the printer.
thaks a million
 
Great!! Forget my other post about that Dutch Canon site then. Also nice to see you found the solution yourself ;-)

---

