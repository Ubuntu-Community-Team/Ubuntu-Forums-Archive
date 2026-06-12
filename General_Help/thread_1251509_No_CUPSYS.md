---
title: "No CUPSYS"
date: 2009-08-27
forum: General Help
---

### Post by JeffPC on 2009-08-27
Hi ubuntu gurus,

I ama freshly minted Ubuntu user and am trying to install my hardware devices.  I have a Brother MFC-465CN on my network.  The UBuntu print thingy (is it CUPS?) found the printer but the Brother doesn't print what its told to.  SO i"ve donloaded a CUPS wrapper and an LPR from Brother, but they don't install properly.

I thought I'd stop the CUPS server and try again.  A little browsing gave me this command:

sudo /etc/init.d/cupsys stop

the response is: sudo: /etc/init.d/cupsys: command not found

I've tried a few variants but no command there!

when I go to /etc/init.d and ls.  I find no "cupsys", but I do find a "cups".  Substituing "cups" for "cupsys" in the above command doesn't work.  also I can't ls to "cups", so I presume its a file:

ls -l cups
-rwxr-xr-x 1 root root 2526 2009-04-17 19:16 cups

So,anyone have any ideas on how to turn off the CUPS server so I can try to reinstall the brother driver?

Thanks,
Jeff P-C
Ubuntu newb

---

### Post by jared.j on 2009-11-12
I am having the same problem and have no idea how to restart it if the file does not even exist. I did find the cups one.

Also I can not get the Web Interface to work remotely no matter what I do. In Firefox it comes up with a problem loading page message and in IE in says it cannot display the web page.

I am entering the address by <ip address>:631

Do I need to enter it with a server name?

---

