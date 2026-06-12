---
title: "LAMP on Desktop Edition"
date: 2010-01-31
forum: General Help
---

### Post by Bartly on 2010-01-31
I just installed 9.10 desktop and wanted to install LAMP. My first efforts after reading a couple articles did not work:

barry@barry-laptop:~$ sudo tasksel install lamp-server^
 Did not work.

barry@barry-laptop:~$ sudo apt-get install lamp-server^
Did not work.

sudo apt-get install apache2
Did not work. 
All of the above returned info that the package or tasks could not be found. Perhaps these are wrong ? 
Well, I did this and it worked:
sudo tasksel

Then I just selected the LAMP server option from the list, and presto, all is well.
Yes I am a newb, but maybe this will other newbs as well.

---

