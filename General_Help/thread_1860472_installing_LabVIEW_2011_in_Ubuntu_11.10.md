---
title: "installing LabVIEW 2011 in Ubuntu 11.10"
date: 2011-10-14
forum: General Help
---

### Post by pwnapple on 2011-10-14
Hi all,

I'm a bit new to ubuntu and would like to use it as a nice programming environment.

I am having A LOT of trouble installing LabVIEW 2011 on Oneiric and was wondering if anyone can help.

Apparently the install DVD for Linux/OSX is HFS+ format and I was able to mount it to a directory I made (~/labview).

However, once it was mounted, it became protected and read-only. I can see the folder has the the labview *.pkg, drivers, etc., but I can't 'cd'  to the directory and run any of them.

ANY help would be appreciated. Thanks in advance and hopefully I can have this installed by tonight!

-sam

---

### Post by kurty_77 on 2011-10-15
have you tried modifying the permissions on the mounted folder?

---

### Post by pwnapple on 2011-10-15
I managed to make some progress yesterday and was able to perform ./INSTALL.

however, I get a ELFCLASS64 error. I tried following this post
[http://forums.ni.com/t5/LabVIEW/labview-for-linux-Ubuntu-64-bit/td-p/1106325/page/2](http://forums.ni.com/t5/LabVIEW/labview-for-linux-Ubuntu-64-bit/td-p/1106325/page/2)

and still no luck (even after installing the libbz package for 32 bit). Am I doing something wrong?

---

### Post by pwnapple on 2011-10-15
alright guys.

I've seen to successfully install LABVIEW 2011 with a few problems.

After installing, I can still see my icon and everything in the applications folder but it does not run. I'm worried that this has something to do with unmounting after i completed the install..

---

### Post by jagrolet on 2012-02-17
I'm pretty new to Ubuntu so I'm not sure about your mounting issue, however I managed to install it sucessfully like this:

I copied the contents of the CD to /home/user/labview/
The packages are in an .rpm format intended for Redhat which is the officially supported release.

Using terminal I navigated to that folder.
Then I used Alien to convert the .rpm packages to .deb packages
alien -c *.rpm 
The -c switch includes the scripts and stops the scripts warnings I got the first go around.
This took about 10 min to complete.

After that I installed all the .deb packages using:
sudo dpkg -1 *.deb

I then entered "labview" at the command prompt and it launched with no problems.
I have loaded several example .vi's and everything seems to run as expected, but I have not fully tested every aspect of the program.
BTW it also added a National Instruments catagory to my launch menu, with Labview in it.

Hope this helps somebody, but again I'm new to this and this may not work for all systems.

---

