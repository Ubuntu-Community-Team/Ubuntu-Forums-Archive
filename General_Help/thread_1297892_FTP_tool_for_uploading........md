---
title: "FTP tool for uploading......."
date: 2009-10-22
forum: General Help
---

### Post by abhilashm86 on 2009-10-22
which is best and efficent tool for FTP? i want to use in ubuntu, i heard about filezilla, but it works on windows, i hate going to CPanel and uploading, which is better..............

---

### Post by ColdFFF on 2009-10-22
Filezilla is available for Ubuntu as well.

sudo apt-get install filezilla

Alternatively you can click Places-> Connect to Server..., select FTP(with login), and enter the ftp server details there, and transfer files in the same way as you would drag and drop files between local folders.

---

### Post by abhilashm86 on 2009-10-22
> **ColdFFF said:**
> Filezilla is available for Ubuntu as well.

sudo apt-get install filezilla

Alternatively you can click Places-> Connect to Server..., select FTP(with login), and enter the ftp server details there, and transfer files in the same way as you would drag and drop files between local folders.

yes filezilla is working great, thanks, but i din't get places->connect server to work, very less options in that, i'm happy with filezilla:)

---

### Post by ColdFFF on 2009-10-22
To be honest I wouldn't recommend using Connect to Server, I only suggested it as another, although horrible, option.

You could also try out other ftp clients by typing ftp in the search bar of synaptic, and installing/trying out the different options that way.


I actually use svn to transfer files to my server: new branch, develop and test locally, merge into trunk, copy trunk to beta site, more testing, copy trunk to live site. This is a pita but very useful when there is multiple people working on the same site.

---

