---
title: "/tmpftpDebugLog.txt (Permission denied)"
date: 2010-10-28
forum: General Help
---

### Post by balaji31d on 2010-10-28
Hi,

My ISP is Starhub and i am located in Singapore. When i try to find my Internet speed by going to [http://utilities.starhub.com](http://utilities.starhub.com) using Firefox, it downloads a Java Applet where i can click on start to test the download speed.

When i click on start i get an error message "
An Error was encountered when running the FTP Command: 
/tmpftpDebugLog.txt (Permission denied)"

Any help would be very much appreciated.

Thanks
Balaji M

---

### Post by gmargo on 2010-10-28
> **balaji31d said:**
> 
/tmpftpDebugLog.txt (Permission denied)"

If' there's really no slash after the /tmp, i.e. /tmp[COLOR=Red]**/**[/COLOR]ftpDebugLog.txt, then something's misconfigured.  I don't know what, but look for a setting value of "/tmp" which could be changed to "/tmp/". (Update: the utilities web site is not available to non-subscribers, so no way to test from here.)

---

### Post by balaji31d on 2010-10-29
Yeah, There is no slash after tmp. The whole file name is /tmpftpDebugLog.txt
I tried to search for this file to give the permission,but couldn't find it. The file also does not reside in the /tmp folder.

Wait! The account which i used to run this page is a normal user account and i have the root enabled in ubuntu.

Lemme go home this evening and try running this tool from root account. Will update you on the status.

Thanks for the help.

---

### Post by balaji31d on 2010-10-29
[LEFT]The issue was solved and i was able to test the Internet Link by logging in as the root user.
Still unable to guess where the txt file would be located at.

Thanks 
[/LEFT]

---

