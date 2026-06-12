---
title: "Slow USB copy workaround for Ubuntu 10.04"
date: 2012-04-22
forum: General Help
---

### Post by mutex023 on 2012-04-22
This is for people who are using Ubuntu 10.04 and are extremely frustrated with slow copy to USB pendrives or hard disks AND do not want to upgrade their kernels (I read somewhere that Ubuntu-2.6.32-41.88 kernel has this bug fixed) because they do not want to reinstall their wireless and Nvidia drivers .

I've written a simple cmd line tool - **'cpc' **- copy in chunks, which will copy a large file in chunks of 100MB by default. You can also mention the chunk size in MB as an argument.
It basically copies 100MB waits for 5 secs, copies the next 100MB and so on....

It works ! I have tested with a 3.8GB file and it copied it in around 12 mins. I know its slow, but its atleast reliable and DOES NOT freeze your system (unlike the Nautilus copy).

I've attached both the source and binary. Just type - '**./cpc'** in the extracted directory
for usage directions.

IT DOES NOT SUPPORT COPYING OF DIRECTORIES OR RECURSIVE COPYING !

---

### Post by erind on 2012-04-22
Works great, thanks for posting. 

As a side note, is it possible to provide the sleep time (5 secs) as an optional command line parameter ( *from sleep(5) to sleep(argv[4])* ), in case it needs to be changed. Tried to edit the source code but was unsuccessful, (not a C expert).

---

### Post by mutex023 on 2012-04-22
Sure, will work on it

---

### Post by mutex023 on 2012-04-22
> **erind said:**
> 
As a side note, is it possible to provide the sleep time (5 secs) as an optional command line parameter ( *from sleep(5) to sleep(argv[4])* ), in case it needs to be changed. Tried to edit the source code but was unsuccessful, (not a C expert).

Here is the updated version which will take the sleep time as a command line parameter.

---

### Post by erind on 2012-04-23
> **mutex023 said:**
> Here is the updated version which will take the sleep time as a command line parameter.

Perfect! Thank you.

---

### Post by el_chupacabra on 2012-05-09
Great. I've put it into my /bin folder.

It's odd how they are unable to fix this problem. It has been around for years. In fact I've never had an Ubuntu installation in which the copying of larger files to an USB drive/stick was working correctly.:(

---

