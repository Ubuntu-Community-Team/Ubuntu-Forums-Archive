---
title: "Java"
date: 2005-03-08
forum: General Help
---

### Post by Kimm on 2005-03-08
I cant get Java working in Linux... I just installed the JRE from sun's website but LimeWire cant find it. I had to reinstall Ubuntu a few days ago... but before that I had some other Java... I think I found it here at this forum somewhere, Blackdown or something, I've made searches for it but I cant find anything. I remember that after I had installed that on my computer everything started working, LimeWire found it, java applets in Mozilla worked and everything. But now I cant find it anymore...

Perhaps someone can help me find it... or knows how I can get normal java running...

---

### Post by Jad on 2005-03-08
Q: How to install J2SE Runtime Environment (JRE)?
Answer ->

[http://www.ubuntuguide.org/#jre](http://www.ubuntuguide.org/#jre)

---

### Post by Kimm on 2005-03-09
thanks, that worked perfectly! :D

---

### Post by Gena on 2005-03-10
I'm having the same problem as Kimm.
I followed the instructions provided in the Starter Guide (thanks for the link) and still have a problem.
Bear with me, please -- I am a very, very new user (1 day) to Linux .

I followed the instructions to this point:

sh jre-1_5_0_02-linux-i586-rpm.bin

I get the license agreement text.  I Accept these terms and then get the following error:
---------------
Extracting...
UnZipSFX 5.42 of 14 January 2001, by Info-ZIP (Zip-Bugs@lists.wku.edu).
  inflating: jre-1_5_0_02-linux-i586.rpm
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - No such file or directory (2)
error: cannot open Packages database in /var/lib/rpm

Done.
--------------

I continued on with the instructions and then the subsequent instructions for installing the JRE for Mozilla FireFox.
It all went well with no additional errors, however, when I do a: java -version
it shows,
bash: java: command not found

and the plug-in doesn't load when I use FireFox (as evidenced by an icon instead of the calendar I am expecting to see)
---
 I feel like I am very close, just missing some very small detail (I hope!).

Thanks in advance,
Gena

---

### Post by Kimm on 2005-03-11
as far as I can tell you have downloaded the wrong .bin file from sun, download the self extracting archive that does not contain a .rpm file and try again :)

---

### Post by pinnockio on 2005-03-12
Hello,


Look at this guid.  You need to install java-package > 0.19.  There is a link on the page for a newer version than the one in Worthy 0.14, but fetching the package from the site doesn't give any errors.

Enjoy [link](http://www.serios.net/content/debian/java.php) 

Kind regards,


Maurits

---

### Post by Psquared on 2005-03-19
I've moved from Fedora to Ubuntu for reasons that are irrelevant here.

I cannot get Java to install. I downloaded the .bin file, version 5.0.02 and followed the instructions in the Ubuntu Guide. 

The file downloads into /home/"username" and when I type ls the file shows up there. I ran the sh command and then used mkdir to create /usr/java. When I try to sudo mv jrel.5.0_02/ /usr/java it tells me the file or directory does not exist. However, it is there plain as day because as I said the ls command shows it. However, it shows up in blue letters which means it is a directory. (the guide does not say anything about this??)

I tried moving the .bin file to /usr/java/ and running the sh command again. It runs, but there are no files or directory created in /usr/java/.

What am I doing wrong here?

---

### Post by pinnockio on 2005-03-20
Hello,


Try the link in my previous post.  It worked for me,... .


Kind regards,


Maurits

---

### Post by Psquared on 2005-03-20
[QUOTE=pinnockio]Hello,


Try the link in my previous post.  It worked for me,... .


Kind regards,


Maurits[/QUOTE]

thanks ..... this is embarassing, but at 2:00 a.m. this morning I figured out that the file name starts jre1 and not jrel.  #-o

---

