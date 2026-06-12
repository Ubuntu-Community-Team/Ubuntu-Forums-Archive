---
title: "gedit fails opening files"
date: 2009-10-11
forum: General Help
---

### Post by 65daysofstatic on 2009-10-11
i get this error at the terminal, when i try to open a file
gedit: symbol lookup error: /usr/lib/libxml2.so.2: undefined symbol: gzopen64

PS.new ubuntu installation with all updates

---

### Post by KlinerDraken on 2009-10-11
> **65daysofstatic said:**
> i get this error at the terminal, when i try to open a file
gedit: symbol lookup error: /usr/lib/libxml2.so.2: undefined symbol: gzopen64

PS.new ubuntu installation with all updates



It is a binary file you can not read it. (well you can open it with nano but its just a bunch of symbols)

---

### Post by 65daysofstatic on 2009-10-11
a binary file?
but it cant open a .txt, a .c ....
when i open gedit and save the file gedit freezes and then closes, and then  i cant open the file .

---

### Post by KlinerDraken on 2009-10-11
> **65daysofstatic said:**
> a binary file?
but it cant open a .txt, a .c ....
when i open gedit and save the file gedit freezes and then closes, and then  i cant open the file .

oh, i thought you were trying to open the /usr/lib/libxml2.so.2 file.

So if you create a new blank text file and call it test.txt gedit will not open it?

---

### Post by 65daysofstatic on 2009-10-11
yup, it closes automatically and when I try to open it the terminal sends that message

---

### Post by KlinerDraken on 2009-10-11
Not sure i'll be able to help you with that but I did find this [_Bug Report_]("https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/211023") but you said it was a new install so i'm not sure if it'll help any.

i'm sure someone smart will come by and be able to help better the me :)

---

### Post by 65daysofstatic on 2009-10-11
thanks anyway, 
the only thing that i remember i installed besides the updates was a zlib because i needed to use the .so but I dont knwo if that could affect gedit.

---

