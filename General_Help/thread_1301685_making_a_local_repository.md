---
title: "making a local repository"
date: 2009-10-26
forum: General Help
---

### Post by tapas_mishra on 2009-10-26
I updated my Ubuntu from command line by using apt-get update as root it is updating packages if I do not wish to connect again and again to internet and want to have a permanent backup of resources on my local machine is it possible some how then how will it be done.

---

### Post by John Bean on 2009-10-26
That's what already happens by default - APT only downloads new/changed packages which are then stored on your PC. If you re-install something it won't download it again unless you've explicitly removed the packages it originally downloaded.

---

### Post by QLee on 2009-10-26
It is as John Bean stated.

If I understood your question correctly then you are asking about the following situation. Those debs reside in /var/cache/apt/archives/ unless you have optioned to "autoclean". That folder can get big after a while and a bunch of updates because old versions remain too. If you "install" and then "un-install" a piece of software the deb for it still is in the archive if you want to install again. 

Or were you looking for a list of installed software so that that the same software could be installed on a new installation?

---

### Post by Bonster on 2009-10-27
you can also use ATPonCD program to back it up

---

### Post by geirha on 2009-10-27
If you have more than one computer running Ubuntu, but only want to download packages from the internet once, you may want to have a look at [https://help.ubuntu.com/community/AptProxy](https://help.ubuntu.com/community/AptProxy)

---

### Post by tapas_mishra on 2009-10-27
Ok thanks for all that support some of the answer added to my knowledge I will check all one by one and come back here.

---

### Post by tapas_mishra on 2009-10-31
> **geirha said:**
> If you have more than one computer running Ubuntu, but only want to download packages from the internet once, you may want to have a look at [https://help.ubuntu.com/community/AptProxy](https://help.ubuntu.com/community/AptProxy)
Thanks I also got an interesting link here [http://ubuntuforums.org/showthread.php?t=352460](http://ubuntuforums.org/showthread.php?t=352460)

---

