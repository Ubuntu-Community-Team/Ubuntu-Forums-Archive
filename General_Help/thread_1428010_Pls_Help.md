---
title: "Pls Help"
date: 2010-03-12
forum: General Help
---

### Post by Lucky3 on 2010-03-12
This is the message i get when i download pretty much any program. I wanted to d/l Comodo Antivirus in this case. I have Ubuntu9.10 and found it to be great so far. I would love to continue using it and appriciate any help.


Archive:  /home/sladjanmastilovic/Downloads/cisfree_installer(2).exe
[/home/sladjanmastilovic/Downloads/cisfree_installer(2).exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/sladjanmastilovic/Downloads/cisfree_installer(2).exe or
          /home/sladjanmastilovic/Downloads/cisfree_installer(2).exe.zip, and cannot find /home/sladjanmastilovic/Downloads/cisfree_installer(2).exe.ZIP, period.

---

### Post by Enigmapond on 2010-03-12
I would suggest, if you don't have a Windoze partition, that you don't even need this programme. It's unlikely you will ever use it as viruses are virtually non-existent in Ubuntu. If you feel you need one get clamav and clamtk from the repositories. Comodo Antivirus is a decent programme for Windoze but...Ubuntu isn't Windoze...:)

```
sudo apt-get install clamav clamtk
```

---

### Post by DawieS on 2010-03-12
The file you are downloading, is a compressed version (.zip) of a Windows executable file (.exe). You will not be able to install these in Linux, only in MS Windows types of operating systems.

Look for Linux versions of these applications. They generally have .deb extensions. If you are looking for anti-virus applications to scan Windows folders, try **clamav** and **clamtk **(Can be found using Synaptic Package Manager).:grin:

---

### Post by matrix14 on 2010-03-12
You can also use "rkhunter" or Rootkit Hunter... 
Welcome to GNU/Linux world...

---

### Post by Lucky3 on 2010-03-12
ty u guys

---

