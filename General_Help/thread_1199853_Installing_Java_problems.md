---
title: "Installing Java problems"
date: 2009-06-29
forum: General Help
---

### Post by Imoen on 2009-06-29
I'm trying to install java on Ubuntu 8.10. I tried with the package manager but when I try to go to yahoo games it tells me java isn't found. So then I tried by using the add-on manager in Seamonkey and still yahoo says there's no java. So I downloaded java from sun.com and it doesn't seem to work. On their directions it says to do su to root but when asked for a password the password fails although it is the same password I use if I do sudo and then it works fine so I don't know what's up with that. but after the license agreement I get:

Unpacking...
Checksumming...
Extracting...
UnZipSFX 5.50 of 17 February 2002, by Info-ZIP (Zip-Bugs@lists.wku.edu).
  inflating: jre-6u14-linux-i586.rpm
./java_rpm.bin: 438: rpm: not found

---

### Post by jimv on 2009-06-29
Yeah, you don't want the rpm file.  That's for Redhat/Fedora/OpenSUSE.

Try these commands in a terminal after closing Firefox:

sudo apt-get remove open-jdk-jre icedeat6-plugin
sudo apt-get install sun-java6-jre sun-java6-plugin

Then try Yahoo again.

---

### Post by TrashmanL on 2009-08-03
I have the same problem. The only Java I have installed is Sun Java, and I tried reinstalling that, it didn't work. I do have Firefox and Swiftfox installed... Java appears only to work in Firefox proper. But Seamonkey is my fav and I'd prefer swiftfox to firefox. I don't understand why it doesn't work in Seamonkey. If I do about:plugins it appears in the list for all my browsers. Usually if it's not working it doesn't appear there.

---

