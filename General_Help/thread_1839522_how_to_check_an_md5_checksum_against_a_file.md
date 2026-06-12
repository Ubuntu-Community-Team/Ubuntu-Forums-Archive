---
title: "how to check an md5 checksum against a file"
date: 2011-09-05
forum: General Help
---

### Post by DataSpy on 2011-09-05
If I go to a website like [https://help.ubuntu.com/community/Installation/MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD") and downloaded an .iso but there is no .md5 file to compare against how would I check the iso file through the command line against the checksum given?

I know I can md5sum *.iso but checking that checksum against the given checksum seems tedious and prone to error.

Any help greatly appreciated,
thanks in advance!

---

### Post by haqking on 2011-09-05
> **DataSpy said:**
> If I go to a website like [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) and downloaded an .iso but there is no .md5 file to compare against how would I check the iso file through the command line against the checksum given?

I know I can md5sum *.iso but checking that checksum against the given checksum seems tedious and prone to error.

Any help greatly appreciated,
thanks in advance!


You answered your first question with the second part ?

And should work fine see here if you are stuck [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by DataSpy on 2011-09-05
Thanks!

I was just wondering if there was an easier way to compare the checksums.  The only way I can think of is to create the md5 file, paste the checksum from the website into it, and then use: md5sum -c file.iso.md5 to validate it.  I thought there might be a feature where I could check the file by comparing the file against the checksum I could copy off the website like: md5sum checksum file

Thanks for the help :)

---

