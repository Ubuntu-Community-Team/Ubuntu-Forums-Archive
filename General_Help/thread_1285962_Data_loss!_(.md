---
title: "Data loss! :("
date: 2009-10-08
forum: General Help
---

### Post by rekahsoft on 2009-10-08
Hi all, yesterday i was working on getting my new seagate 1 tb drives working and getting them working under a software raid...this is i double clicked enter when i went to make the changes and i added my external 500 gb drive to the softare raid instead of the other 1 tb drive...So it formatted the partition to make room for the software raid. Now my problem is that i had that 500 gb drive packed full of my data...and i would really like to get it back...i have been doing some reading on data recovery but idk if i have a special case...when a drive is formatted afaik the data is not actually removed...i turned off the drive as soon as i realized i made the mistake (2 seconds later..after a unount). Could i use parted to retrieve my data? or gpart? or testdisk? What would be my best option? Thanks for the help/advice :)

---

### Post by cariboo on 2009-10-08
Using testdisk and photorec would be the best way to recover your data. Testdisk is in the repositories, photorec is a part of the testdisk package.

---

### Post by rekahsoft on 2009-10-10
So i did some reading and it seems that testdisk and photorec can't deal with recovering files from a former reiserfs partition :S any ideas on howto recover a reiserfs partition? :S

---

### Post by QIII on 2009-10-10
Well ...

How much is the data worth to you?

---

### Post by rekahsoft on 2009-10-10
max 3 hours time wise...no professionl work..its 500gb of media...all re-download-able but thats a pain :(

---

