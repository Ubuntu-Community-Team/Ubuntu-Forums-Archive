---
title: "getting files from phone"
date: 2009-11-10
forum: General Help
---

### Post by cmscott2 on 2009-11-10
Im trying to get files from my phone via usb on ubuntu and for some reason its not reading the usb. I have an sd disk and the phone and the phone is an lg cu720 shine.  The usb drive works fine with other isb hook ups. 

help please!! thanks!!

---

### Post by rapsodia on 2009-11-10
im not sure about your phone but for my android phone i have to make sure i enable "usb drive" on the phone otherwise all it does its start charging instead of presenting itself as a mass storage device which then ubuntu can mount. 

let me know if that helps

---

### Post by cmscott2 on 2009-11-10
Yeah theres no setting on there that enables the usb drive, I tried to open it on virtual son and it recognizes the usb but it wont let me get to it under devices, it never pops up. and it just forces th e phone to keep turning off and on..... maybe its haunted lol

---

### Post by rapsodia on 2009-11-10
ok connect your phone like you always do the following in terminal and post back the result

dmesg

sudo fdisk -l

---

### Post by ChirpE on 2009-12-26
> **rapsodia said:**
> im not sure about your phone but for my android phone i have to make sure i enable "usb drive" on the phone otherwise all it does its start charging instead of presenting itself as a mass storage device which then ubuntu can mount. 


Android has this under Settings > Applications > Development > USB Debgging.

I'd never normally go here, but after allowing USB Debugging and then connecting it to my laptop my phone (G1) asked if I wanted to mount it. Once I did I could fully access the files and easily delete unwanted stuff.

---

