---
title: "efix creates bad tiff files"
date: 2011-09-05
forum: General Help
---

### Post by qrajive on 2011-09-05
Hi,
 
I recently went from RH to Ubuntu 10.0.4 LTS server.
 
One functionality I have on this machine is a script which faxes ordinary text files using the efax package.
 
I first run efix -i text textfile.txt > tiff_file.tiff
 
This has worked for years on RH. When I create dmy new server with Ubuntu and installed the latest efax package it stopped working. No error mesages, nothing. 
 
However when looking very carefully on the output I could see the text far up in the upper left corner. Each line of my text file was about 0.1 mm high or less. 
 
I tried a number of options and searched the internet like crazy. No remedy. Not even one reference to this problem.
 
Finally I copied the efix executable from my RH machine to my new Ubuntu server and now it works again.
 
There is a slight difference in size between the two executables. But from what I understand they both claim to be the same version. It seems efix has not changed in years (or even decades).
 
Has anyone else seen this problem and found a better solution?
 
Kind regards,
Hans

---

