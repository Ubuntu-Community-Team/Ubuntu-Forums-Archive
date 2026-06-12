---
title: "mlabel - strange characters after renaming"
date: 2011-06-23
forum: General Help
---

### Post by vian on 2011-06-23
Hi all,

although I am not an Ubuntu user, hopefuly I'll find someoe to give me a hand. 
I am experiencing problem with mlabel command. It works ok, but after renaming my USB key to (for example) SANDISK I am getting this CLI output:

[I]
[root@localhost ~]# mlabel -i /dev/sdb1 -s ::SANDISK
 Volume label is SANDISK (abbr=SANDIS~1~À_)
[root@localhost ~]# sudo mlabel -i /dev/sdb1 -s ::
 Volume label is SANDISKoîÀ2
[root@localhost ~]# 
[/I]
Of course the name of the USB key is then displayed incorrectly - with those strange characters behind.

My locales are all set as follows:
[I]
[root@localhost ~]# locale
LANG=en_GB.utf8
LC_CTYPE="en_GB.utf8"
LC_NUMERIC="en_GB.utf8"
LC_TIME="en_GB.utf8"
LC_COLLATE="en_GB.utf8"
LC_MONETARY="en_GB.utf8"
LC_MESSAGES="en_GB.utf8"
LC_PAPER="en_GB.utf8"
LC_NAME="en_GB.utf8"
LC_ADDRESS="en_GB.utf8"
LC_TELEPHONE="en_GB.utf8"
LC_MEASUREMENT="en_GB.utf8"
LC_IDENTIFICATION="en_GB.utf8"
LC_ALL=en_GB.utf8
[/I]

As seen above the problem is a couple of strange characters in the new name. Been trying to find a solution using google but no luck so far.

This image speaks volumes (it is the USB key icon on the desktop):

[IMG]http://heredy.net/images/usb.jpg[/IMG]

My system is Mandriva 2010.2, XFCE, Mtools version 4.0.13. I would be grateful for any help. 

Thanks, Ivan

---

### Post by vian on 2011-06-24
Hi again. So I am answering to myself (and someone in the future having the same problem and reading this thread): The solution is to fill in all the 11 characters in the name (or adding spaces) and the result is as required.

Simply said all the 11 characters must be used.

**Edit:** 
One more detail if you want to use a name with less than 11 characters: It must be in quotes and remaining missing characters must be "spaced", e.g. for SANDISK use "SANDISK+4xspace" which gives 11 characters together.

Thanks to [this forum]("http://www.abclinuxu.cz/poradna/linux/show/338726") for solving the issue.

Ivan

---

