---
title: "File transfer - asci conversion - corrupted files"
date: 2009-07-06
forum: General Help
---

### Post by mahanare on 2009-07-06
Dear all,

Recently I happen to re-install ubuntu 9.04 in my laptop. To make a backup of my data in laptop, I pushed all important data to desktop using ftip client Fillezilla. 

Desktop runs with windows xp and laptop with ubuntu 9.04.  But during the transmission, there is some conversion problem and I am not able to view the pdf files, image files any more. It says something abt asci conversion corrupted files.

Is anyone aware of any solution to get ths orginal content back. Please do let me know.

In case if there is a different website/forum to get appropriate help please point me towards the same.

Thanks a ton
Harinath Mallepally

---

### Post by jonobr on 2009-07-06
Hello


I dont think I have a good answer for you, just a possible reason for the problem.

When doing an ftp the default mode is usually ascii and you can change it to binary.

Changing to binary transfers the information as raw data and ascii is used for transferring files that have ascii formatting, such as text files etc.

Im thinking that you may have copied the files in the wrong format and this could be unrecoverable...

Grabbing from a different site it explains

> If a file containing binary data is sent using ASCII mode, it will most likely end up being corrupted. If you're having problems with corrupted file transfers, try using binary mode when transferring the file. Some common file formats that are sometimes mistakenly transferred in ASCII mode includes:
* pdf - PDF files can contain embedded binary data such as images.
* doc - Microsoft Word documents are a binary formatted file.
* In general, all audio, video, and image file formats are binary.

---

### Post by mahanare on 2009-07-07
Thank you jonobr for replying me. yes looks like i do not have choice. But will try to keep the corrupted fileset for some more time and see if i can fix them and use.

---

