---
title: "problem with package management"
date: 2012-08-31
forum: General Help
---

### Post by lou21 on 2012-08-31
Hi

I have a problem and I don't know how to fix it... I'm hoping someone can help.

I was away from any internet for about a month. When I returned I had various updates that needed to be installed which I allowed. However now the apt-get command is not working. 

sudo apt-get update gives:

Reading package lists... Error!
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.


sudo apt-get install package-name gives:

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

sudo apt-get upgrade gives the same error message

Oh and the the GUI package management program does not open at all.

What do I need to do?

Thank you in advance for any help!

---

### Post by drmrgd on 2012-08-31
Try running:

```
sudo rm -rf /var/lib/apt/lists/*
```

Then rebuild by updating and trying the upgrade again.

---

### Post by lou21 on 2012-09-01
> **drmrgd said:**
> Try running:

```
sudo rm -rf /var/lib/apt/lists/*
```Then rebuild by updating and trying the upgrade again.

Worked perfectly

Thank you.

---

