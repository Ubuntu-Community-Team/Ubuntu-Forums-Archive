---
title: "external harddrive"
date: 2010-09-13
forum: General Help
---

### Post by JBless on 2010-09-13
ok, so yesterday my computer (sort of) broke, it says it cant find my hard drive, so i plugged in another hard drive to see if that was the problem, it didnt work. my best guess is that either the cords that connect the hard drive to the motherboard went bad or there is a loose connection somewhere. So what i did to fix the problem was i just booted from the ubuntu disc and hit try ubuntu, so i can use the internet but i dont have any hard drive. I went down to my basement to find that i have a 500 gigabyte seagate external hard drive, i plug it in and ubuntu doesnt autofind it like it does anything else, so my question is how do i install this external hard drive, if at all possible

---

### Post by jquis8411 on 2010-09-13
I would say at this point  the best first step would to be trying to figure out why your computer didn't find your hard drive to begin with. Can you open the case and make sure everything is plugged in? Make sure the controller is fully plugged in Also the exact error you got and type of HDD would help.

---

### Post by CharlesA on 2010-09-13
If it's not being found automatically, try running this from a terminal:

```
sudo fdisk -l
```

---

### Post by JBless on 2010-09-16
@jquis8411
i looked for all lose connections and couldnt find any, it is possible that i missed one but i doubt it, i will probably get someone better with computers to look at it
@CharlesA
the problem isnt the operating system finding the hard drive its the computer finding the hard drive.

@both
that you for answering, but i still just want to know how to install an external hard drive

---

### Post by CharlesA on 2010-09-17
Ok. Are they USB drives?

Do they work on another computer?

It could be a few things, but the first thing I would do would be to try it on another machine and see if it works on that one.

---

### Post by JBless on 2010-10-09
ok, so i just found out (my dad told me), that one has been broken for years, but today i just bought one of those external harddrive cases, that you can put a real hard drive in to access the files while i run off of a disk, when i plug it in and turn it on nothing happens, when i try the sudo fdisk command you told me to use it finds the external hard drive but i still dont know how to access it.

---

