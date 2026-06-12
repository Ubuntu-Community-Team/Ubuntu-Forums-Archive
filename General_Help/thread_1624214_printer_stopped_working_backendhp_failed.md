---
title: "printer stopped working backend/hp failed"
date: 2010-11-17
forum: General Help
---

### Post by John_Rose1 on 2010-11-17
I installed Ubuntu 10.4 (32 bits) on my new Dell Vostro 3700 portable about a month ago, and the HP 5500 All in One printer was worked fine without any special configuration (I don&#8217;t know whether it was using cups, I didn't even know what it is). A couple of days ago I configured a dummy printer to generate pdf files as per recommended for 9.4 at [http://*************/hub/Print-to-PDF-in-Ubuntu-904]("http://*************/hub/Print-to-PDF-in-Ubuntu-904"). There was problem with file access because of a Ubuntu 10.4 bug, and I had to use advice at [https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/472468](https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/472468) to change the permissions for cups:
 sudo chmod 700 /usr/lib/cups/backend/cups-pdf
sudo chmod 700 /usr/lib/cups/backend
 
After that pdf generation worked fine, but printing to the HP 500 stopped working (jobs stay in the queue with an error message &#8220;[COLOR=#000000]/usr/lib/cups/backend/hp failed&#8221;[/COLOR]. I saw several different situations on the net in which this error occurred, and tried the different fixes even though not sure that the situations corresponded exactly to my case (none mentioned that the problem started after pdf printer configuration). Thus:
 i) According to [http://ubuntuforums.org/showthread.php?t=1526070](http://ubuntuforums.org/showthread.php?t=1526070) I installed the HP Device Manager but and tried printing test page from there.
 ii) According to [https://bbs.archlinux.org/viewtopic.php?id=85454](https://bbs.archlinux.org/viewtopic.php?id=85454) someone said a similar problem was solved by installing &#8220;avahi daemon&#8221;. Mine was already installed in the Package Manager, but I updated it.
 Iii) Then I found another site ([http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=556406](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=556406)) that fixed a similar problem with Debian with &#8220;sudo apt-get install gs-esp&#8221; which I, probably stupidly, tried.
 
I still can't print. The computer communicates fine with the printer for checking the ink level and for scanning, but print jobs stay in the queue. The pdf generation printer still works fine. Could someone please help?

---

### Post by tarnall on 2011-02-12
I had a similar problem... one day my Epson printer did not work with UBUNTU...I have been installing the updates as the come.  I had to delete the printer from the system and reinstall it to make it work again...  HUMMMMMMMMMMMMMMMMMMMM

About a year ago I introduced a friend of mine to UBUNTU/Win7 double boot.  She ended up with a virus in Win 7 so I suggested she use UBUNTU. A couple of weeks ago her printer stopped working too in UBUNTU, but ok in Win 7.

I am wondering if some of the updates to UBUNTU has caused some printer problems???????

Terry
Hayward, CA

---

