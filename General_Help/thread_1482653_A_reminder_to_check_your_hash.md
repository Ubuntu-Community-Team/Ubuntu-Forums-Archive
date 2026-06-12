---
title: "A reminder to check your hash"
date: 2010-05-13
forum: General Help
---

### Post by colorlessprism on 2010-05-13
ive noticed lately people's md5's have  not been matching up, this can   cause any number of errors from install to boot failures. i had to   download 10.04 three times before the  checksums matched.
   md5 is one of the most common signatures  to make sure that a  file that   you have downloaded is not corrupt. once  you have downloaded the the   ISO, we need to get the checksum of the file on your   computer.  then  make sure that our checksum matches the one on the website (*see below) . if the checksum matches, then  your file is   exactly the same on your computer as it was/is on the  server. it is a   very good idea to  run an md5 hash  comparison when you have a  file, like an OS install  CD, that has to  be 100% correct.
       **if you are using**   **XP (or any other windows operating  system)** you need to use a program to calculate the checksums.[winMD5Sum]("http://www.nullriver.com/products/winmd5sum") is an open source program that does well and will calculate the MD5    checksum of a file or an ISO image. 
         **if you are using Linux** you should be able to open a terminal, go to  the directory that has the file you want  to check and run the "md5sum" command:[INDENT][FONT=Courier New]*cd /your/download/directory*
*  md5sum <your file name should be here.iso>*
[/FONT][/INDENT][FONT=Verdana]it should print something like this[/FONT]:[INDENT][FONT=Courier New]*712277c7868ab374c4d3c73cff1d95cb ubuntu-10.04-netbook-i386.iso*
[/FONT][/INDENT]once you have verified the hash, burn the ISO to CD, boot from the CD and select to test its integrity from boot screen.

**Compare the result your computer calculated with the corresponding hash:*
[http://releases.ubuntu.com/10.04/MD5SUMS:](http://releases.ubuntu.com/10.04/MD5SUMS:)
a54366aa72d6b576ee8fc0215f8a13b9 *ubuntu-10.04-alternate-amd64.iso
5b2dadacfd692b4f2d5c7cf034539262 *ubuntu-10.04-alternate-i386.iso
3e0f72becd63cad79bf784ac2b34b448 *ubuntu-10.04-desktop-amd64.iso
d044a2a0c8103fc3e5b7e18b0f7de1c8 *ubuntu-10.04-desktop-i386.iso
0b0e0d36050d9980ec995262eb9f2e6b *ubuntu-10.04-netbook-armel+dove.img
9e0d6ac7b69bb7912d49369a6807e39d *ubuntu-10.04-netbook-armel+imx51.img
712277c7868ab374c4d3c73cff1d95cb *ubuntu-10.04-netbook-i386.iso
8ee25c78f4c66610b6872a05ee9ad81b *ubuntu-10.04-server-amd64.iso
15342636441181f7a19c65984b44e24c *ubuntu-10.04-server-i386.iso
e81f931b1de017520f6d4aa4f78c5c8b *wubi.exe

---

