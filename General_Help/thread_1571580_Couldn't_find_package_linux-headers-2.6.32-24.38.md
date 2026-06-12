---
title: "Couldn't find package linux-headers-2.6.32-24.38"
date: 2010-09-09
forum: General Help
---

### Post by TomFumb on 2010-09-09
Hi, I'm having issues compiling compat-wireless and so far not been able to figure out the problem.  I am not exactly what you would call a linux expert...

I originally tried to compile using the 'make' command, which returned this error:

make: *** /lib/modules/2.6.32-24.38/build: No such file or directory.  Stop.

I googled this and figured I didn't have linux headers installed, so I did 'sudo apt-get install build-essential', which completed fine.  However I still get the same error message, so after a bit of googling I went for 'sudo apt-get install linux-headers-$(uname -r)'.  This returns the following error message:

Couldn't find package linux-headers-2.6.32-24.38

I have enabled all software sources through the sources gui and run an update & upgrade, and still no joy.  Using 'make' still gives me the 'no such file or directory' message above.

Any suggestions would be very much appreciated!

I'm using a Ubuntu VM I got from Sourceforge which is fully up to date.

---

### Post by TomFumb on 2010-09-09
additional note:

/lib/modules/2.6.32-24.38/build does infact exist as a sym link but it's broken (i.e. what it's supposed to point to doesn't exist).  I tried to find where it was supposed to point to with 

sudo updatedb; locate 2.6.32-24

but got nowhere.

I have installed the 2.6.32-24-generic linux-headers now but still getting nowhere.  Someone please help!

---

