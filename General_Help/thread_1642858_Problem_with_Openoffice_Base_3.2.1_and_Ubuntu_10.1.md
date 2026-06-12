---
title: "Problem with Openoffice Base 3.2.1 and Ubuntu 10.10 x64"
date: 2010-12-10
forum: General Help
---

### Post by cscj01 on 2010-12-10
I am having a significant performance problem with Openoffice Base under Ubuntu 10.10 x64 and OO 3.2.1 with a MySQL database. Loading is slow (several seconds), moving from record to record is slow (even longer), search seems to parse about 5 records per second, everything is slow. Everything was fine in Ubuntu 10.04 and OO 3.2.0

Additionally, I have the problem of adding a new record to a table in a subform and receiving the message "Error inserting the new record. No value specified for parameter 1". When I do this, I can quit without saving the data, reopen the form, and the added record is there. If I press OK on the message and try to move the focus to a field in the form, I get the message again. In that case, if I quit without saving and reopen the form, I have two identical records in the subform.  I have tried this last sequence up to seven times (get message, press OK, move focus to forrm, etc.) and have gotten seven identical records, so it would seem to be a bug in the build.  My research to this point shows that this only occurs for people with Ubuntu 10.10 and Openoffice 3.2.1.  I had no such issues in Ubuntu 10.04 and OO 3.2.0.  I have made no changes to the forms or the database.

I would like to use an earlier Ubuntu build of Openoffice that worked for me before, such as 3.2.0, but I am unsure how to downgrade the Ubuntu version of Openoffice.  I have read that Ubuntu uses a special make of OO called GO-OO or a subset of GO-OO (I think). Because of this I am not sure how to approach solving this problem.  I do not want to install the native Openoffice, nor the version from the GO-OO site.

Does anyone have any suggestions on this?

---

### Post by bccoulomb on 2010-12-11
I have the same problem now I have installed Ubuntu 10.10.
I still have my old HDD with 10.04 and the earlier version of OO and that is fine.
Is this a recorded bug? Will it be dealt with soon?
I am on AMD 64 dual.
bccoulomb

---

### Post by squenson on 2010-12-11
Based on bccoulomb's message, it seems to be a bug. I suggest that you search the OOo bug database at [http://qa.openoffice.org](http://qa.openoffice.org) to see whether it is recorded and then you can add it (you need to register but it's free).

Knowing the time between two releases -- about 6 months -- I doubt you will have a fix before June 2011, so you should consider downgrading to OOo 3.2.0 or test the official release.

---

### Post by cscj01 on 2010-12-11
> squenson:

Knowing the time between two releases -- about 6 months -- I doubt you will have a fix before June 2011, so you should consider downgrading to OOo 3.2.0 or test the official release. 

Ok, I'll check that link for the OOo bugs.  In the meantime, can you tell me the steps to downgrade to 3.2.0.  I think i can use the following command to get rid of 3.2.1:

sudo apt-get remove openoffice*

Where can I find the debs for the Ubuntu build of 3.2.0?  Is there an install order so that all dependencies are satisfy?  Thanks.

---

### Post by cscj01 on 2010-12-13
bump

---

### Post by zerubbabel on 2010-12-15
You can get OpenOffice 3.2.0 [here]("http://download.openoffice.org/other.html").

---

### Post by NCLI on 2010-12-15
> **zerubbabel said:**
> You can get OpenOffice 3.2.0 [here]("http://download.openoffice.org/other.html").
From the link, download the "Linux 32-bit Intel DEB" if you have the 32-bit version of Ubuntu, and the "Linux 64-bit Intel DEB" if you have the 64-bit version.

You can find out what version you have installed by opening the terminal and running this command:
```
uname -a
```
If you don't see this somewhere in the output, you have the 32-bit version:
```
x86_64 GNU/Linux
```

---

### Post by cscj01 on 2010-12-16
> Originally Posted by zerubbabel
You can get OpenOffice 3.2.0 here.

The US English download is 3.2.1.  I see 3.2.0 in other languages, but that does me no good.

I have looked in the Scribblers PPA, in the Lucid packages at Ubuntu, and several other places, but I can't seem to find 3.2.0.

---

### Post by Aelwyn on 2010-12-17
I'm having similar problems, the program is slow to the point of being unusable. I have a small and very simple HSQL database. I also tried to upgrade to the latest release candidate of LibreOffice, but this didn't help.

---

### Post by cscj01 on 2010-12-18
I have finally got this performance problem resolved.

Go to this link: [http://www.unixmen.com/linux-distributions/4-ubuntu/1266-how-to-install-latest-java-version-in-ubuntu-1010-maverick-meerkat-via-ppa]("http://www.unixmen.com/linux-distributions/4-ubuntu/1266-how-to-install-latest-java-version-in-ubuntu-1010-maverick-meerkat-via-ppa")

I already had Canonical Partners activated.  I then entered the next 3 sets of commands.  In the last set, I chose the Sun JRE.

Then I started Openoffice, went to Tools/Options/Java.  It showed I had two JRE's, 1.6.0_22 and 1.6.0_20.  I chose 1.6.0_22.

Once again I restarted Openoffice, and all was well wrt performance.  I have not tried to add a record in a subform as yet, but I will do that tomorrow.  I will report back on the success or failure of a fix for the error message mentioned in my original post.

I hope this helps Aelwyn and bccoulomb.

---

### Post by Aelwyn on 2010-12-18
Thank you very much, it worked for me as well :D

---

### Post by bccoulomb on 2010-12-18
Thanks cscj01
That solved my problem.
Great to have people like you around.
bccoulomb.

---

### Post by cscj01 on 2010-12-18
> **bccoulomb said:**
> Thanks cscj01
That solved my problem.
Great to have people like you around.
bccoulomb.

> **aelwyn said:**
> Thank you very much, it worked for me as well

You're welcome.  Next, I tried adding a record in a subform and received the same error message.  So I'll keep looking for that issue.  At least the performance problem is fixed.  So I think I'll mark this thread as solved and start a new thread for the error message.

---

### Post by ugm6hr on 2010-12-27
> **cscj01 said:**
> I hope this helps Aelwyn and bccoulomb.

And me! Thanks.... I'd been unable to collect data for over a week - looks resolved by this.
This is a real problem for enterprise use - shame on Ubuntu :(
Better get back to work - have some catching up to do.
Did anyone submit a bug to launchpad?

---

### Post by cscj01 on 2011-02-23
Well, my problem is back with a vengeance.  I upgraded to Java 1.6.0.24 from 1.6.0.22 and the madness begins again.  I need to regress to 1.6.0.22.  Does anyone know how to do this?

---

### Post by cscj01 on 2011-02-24
bump

---

### Post by scouser73 on 2011-02-24
Can I recommend that you remove OpenOffice entirely and install LibreOffice.

If you wish to do so, then the instructions are as follows:

Firstly remove OpenOffice with this command

**> sudo apt-get remove openoffice*.***

1 - Download LibreOffice from: [http://www.libreoffice.org/download]("http://www.libreoffice.org/download")

Make sure to select **.deb** from the dropdown menu

2 - Extract the file to ~/Desktop

3 - Rename the file to libreoffice

4 - Open Terminal and enter this command:
Quote:
> sudo dpkg -i ~/Desktop/libreoffice/DEBS/*.deb


5 - Then enter the following command into Terminal:
Quote:
> sudo dpkg -i ~/Desktop/libreoffice/DEBS/desktop-integration/libreoffice3.3-debian-menus_3.3-9526_all.deb


You have now successfully installed LibreOffice.

**_LibreOffice Language Pack Installation_**

1 - Visit [http://download.documentfoundation.org/libreoffice/testing/3.3.0-beta2/deb/x86/](http://download.documentfoundation.org/libreoffice/testing/3.3.0-beta2/deb/x86/)

2 - Find the Language pack for your locale and download

3 - Save to your desktop

4 - Right click and select Extract Here

5 - Rename the extracted folder to libreoffice

6 - Open Terminal and copy & paste the following commands:

cd Desktop

sudo dpkg -i libreoffice/DEBS/*.deb

You have now installed the LibreOffice Language Pack for your locale.

---

### Post by cscj01 on 2011-02-25
I have actually resolved this by removing 1.6.0_24 of Sun Java and installing 1.6.0_21.  I believe there is something related to Sun Java 1.6.0_22 and 1.6.0_24.  Just a suspicion since both caused the performance problem.

---

### Post by rdh61 on 2011-03-08
I am having the same trouble after upgrading from java-6-sun-1.6.0.22 to java-6-sun-1.6.0.24. How can I reinstall the previous version? When I try:

sudo apt-get install java-6-sun-1.6.0.22

I am told:

Couldn't find package java-6-sun-1.6.0.22

Thanks for your help.

---

### Post by ugm6hr on 2011-04-06
> **cscj01 said:**
> I have actually resolved this by removing 1.6.0_24 of Sun Java and installing 1.6.0_21.  I believe there is something related to Sun Java 1.6.0_22 and 1.6.0_24.  Just a suspicion since both caused the performance problem.

Indeed - both OO and LibreOffice don't appear to like 1.6.0_24 (or 1.6.0_20).
I don't have the original .deb for the older version.... Has anyone?

---

### Post by cscj01 on 2011-04-11
Sorry, I've been out of pocket.  Try this link: [https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=jre-6u21-oth-JPR@CDS-CDS_Developer]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=jre-6u21-oth-JPR@CDS-CDS_Developer")

---

### Post by cscj01 on 2011-04-15
Also, see this: [http://ubuntuforums.org/showthread.php?t=1694448]("http://ubuntuforums.org/showthread.php?t=1694448")

---

