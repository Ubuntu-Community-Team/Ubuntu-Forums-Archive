---
title: "Cloning windows 7 install onto ubuntu disc"
date: 2012-07-10
forum: General Help
---

### Post by chieferer on 2012-07-10
Hi,

This is somewhat of a convoluted problem but I have a pre-existing windows 7 install on a separate disc than my ubuntu install (12.04).  Id like to move the windows 7 install onto the other disc so i tried cloning the windows 7 partition onto a second primary partition on the disc with ubuntu.  After adding the install to grub and trying it out, I get a "bootmgr is missing" message.  From what I can understand, this has something to do with the 100MB 'system reserved' partition on my windows 7 disc.  Not really sure where to go from here - any help would be appreciated.

---

### Post by analogdialog on 2012-07-10
> **chieferer said:**
> ...  From what I can understand, this has something to do with the 100MB 'system reserved' partition on my windows 7 disc. 

How so ?

---

### Post by wilee-nilee on 2012-07-10
> **chieferer said:**
> Hi,

This is somewhat of a convoluted problem but I have a pre-existing windows 7 install on a separate disc than my ubuntu install (12.04).  Id like to move the windows 7 install onto the other disc so i tried cloning the windows 7 partition onto a second primary partition on the disc with ubuntu.  After adding the install to grub and trying it out, I get a "bootmgr is missing" message.  From what I can understand, this has something to do with the 100MB 'system reserved' partition on my windows 7 disc.  Not really sure where to go from here - any help would be appreciated.

Lets get a look at the HD you say disc but I think we are talking about a HD.

Use the bootrepair app the get a bootinfo summary, and post the HTTP of the script.  You may need a windows recovery or install disc to fix this possibly, let us know if you have this. 

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by chieferer on 2012-07-11
So I actually ended up figuring it out.  Turns out the windows bootloader is installed on a separate partition for whatever reason](*,) All I needed to do is move the bootloader software from its own partition to the one with the windows files and change  few registry keys.  If anyonees interested, this is the guide I used: [http://www.terabyteunlimited.com/kb/article.php?id=409](http://www.terabyteunlimited.com/kb/article.php?id=409)

---

