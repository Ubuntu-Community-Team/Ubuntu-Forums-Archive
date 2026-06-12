---
title: "how do i get flash player working?"
date: 2009-09-01
forum: General Help
---

### Post by Kello125 on 2009-09-01
Im new to this, and i need some help. :]

---

### Post by oldos2er on 2009-09-01
Are you running 32- or 64-bit Ubuntu? If 64, use this script: [http://ubuntuforums.org/attachment.php?attachmentid=125745&d=1250873141](http://ubuntuforums.org/attachment.php?attachmentid=125745&d=1250873141)

 If 32, open a terminal (Applications, Accessories, Terminal), and run
```
sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
```This will install Java, Flash, and some other goodies.

---

### Post by blazemore on 2009-09-01
+1 for ubuntu-restricted-extras
When the Java license agreement comes up, hit Tab to get to the OK button

---

### Post by NoaHall on 2009-09-01
If you're using 64 bit, do the same as above, but download the flash from the official site - it's a alpha, but works perfectly!

---

### Post by fluffman86 on 2009-09-01
> **NoaHall said:**
> If you're using 64 bit, do the same as above, but download the flash from the official site - it's a alpha, but works perfectly!

I've been running 64bit Ubuntu for 2 years now and have never had to download flash from adobe, that I can remember.  Maybe under Feisty and Gutsy, but certainly not since Hardy.

---

### Post by NoaHall on 2009-09-01
It works much better with Opera than the one you can get via apt-get .

---

### Post by oldos2er on 2009-09-01
> **fluffman86 said:**
> I've been running 64bit Ubuntu for 2 years now and have never had to download flash from adobe, that I can remember.  Maybe under Feisty and Gutsy, but certainly not since Hardy.

 Then you must be using 32-bit Flash with ndiswrapper. Adobe updated 64-bit Flash around the end of July, it works great, at least for me.

---

### Post by Kello125 on 2009-09-01
> **oldos2er said:**
> Are you running 32- or 64-bit Ubuntu? If 64, use this script: [http://ubuntuforums.org/attachment.php?attachmentid=125745&d=1250873141](http://ubuntuforums.org/attachment.php?attachmentid=125745&d=1250873141)

 If 32, open a terminal (Applications, Accessories, Terminal), and run
```
sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
```This will install Java, Flash, and some other goodies.

Thanks man, you really saved me here.

---

### Post by Kello125 on 2009-09-01
Ok, now i cant use "go back" or  " go forward" 

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
jason@jason-desktop:~$ 


what when wrong and how can i fix this?

---

### Post by blazemore on 2009-09-02
```
sudo dpkg --configure -a
```
Post any errors here

---

