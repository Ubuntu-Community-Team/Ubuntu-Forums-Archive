---
title: "Guide for mounting Nokia phones via bluetooth in nautilus"
date: 2011-11-21
forum: General Help
---

### Post by gagmani on 2011-11-21
Until Mint Team or Ubuntu Team come with solution like Fedora did,we  have to wait for GUI based solution for mounting mobilephones via  bluetooth in nautilus.

Simple Terminal method for doing this:

1) first install **obexfs**.Open a Terminal and type **sudo apt-get install obexfs **
2) Make a folder in your Home directory e.g. **phone**
3) to mount : **obexfs -b your:bluetooth:address ~/phone**
e.g. obexfs -b **aa:bb:cc:dd:ee:ff** ~/phone
4)  Bluetooth address(usually combination of 12 alphabets and numbers) is  what your device is recongnised by other devices.An easy way to find it  is to pair the phone with computer.It shows for sometime during  pairing.If you missed it, then goto System Settings> Bluetooth.  Select your device and in the right pane it will show you the address.
5)  For those who still unable to find it, switch on bluetooth on  mobilephone and type *#2820# on your Nokia phone and it will show you.It  will show it like this **aabbccddeeff**.Just note it and add colon after two letters.
6) For unmounting or removing type

**fusermount --u ~/phone**

Notes: 1) Internet connection is required to get obexfs.
           2) It is a temporary solution.You need to type every time to  mount phone.My suggestion is to save the command with your bluetooth  address to a text file and copy paste from there every time.

---

