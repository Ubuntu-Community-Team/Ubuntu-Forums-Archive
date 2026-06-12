---
title: "Make a script to do..."
date: 2010-02-27
forum: General Help
---

### Post by How_weird on 2010-02-27
Hello,

I have an easy request. I would like to know the proper way to write a script to format a flash drive and then have it download a few .exe files (combofix / malwarebytes /ETC).
Could someone please give me a basic idea or a link to a site that could show me some light.
 
Sorry for posting a simple question, but I have been looking for a few days and have yet to find an answer.

---

### Post by NFblaze on 2010-02-27
I came across this nice tutorial about writing scripts [http://www.calpoly.edu/~rasplund/script.html](http://www.calpoly.edu/~rasplund/script.html), the other day.

Basically what you would need to do is. 

1) Figure out what your going to format the drive into like ntfs,ext3,ext4,fat32. Then find out which program in Linux formats to that type (Perhaps you could use Gparted, it should have command line capabilities) You would also have to figure out how to make sure it doesnt format the wrong device.


2) Figure out the (preferably static) download url addresses of the exes you want. You could probrably use 'wget' for this.


3) Write those commands into a text editor save it and make it executable

---

