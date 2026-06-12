---
title: "DoD CAC with ubuntu 11.10 and Firefox 7.0.1"
date: 2011-11-08
forum: General Help
---

### Post by bsmith12345 on 2011-11-08
[SIZE=1]Hi.
I am trying to get a DoD CAC to work with Ubuntu 11.10 and Firefox 7.0.1. I have the card reader installed and "Pcsc_scan" will show the reader and the card but when I try to open Firefox with the card inserted it will not open. Alternatively, if Firefox is open and I insert the card, Firefox will crash and not restart until the card is removed. 
I have searched google.com and the ubuntu forums far and wide and I cannot find any help. I have also asked this multiple times on #ubuntu irc. If you could offer any help it will be greatly appreciated.[/SIZE]

---

### Post by bsmith12345 on 2011-11-08
mods: you can close this as solved. I figured out that "cackey" is what is needed for 11.10 and ff 7.0.1 to run the reader correctly.

---

### Post by lovinglinux on 2011-11-09
> **bsmith12345 said:**
> mods: you can close this as solved. I figured out that "cackey" is what is needed for 11.10 and ff 7.0.1 to run the reader correctly.

There is no reason to close it. Marking the thread as solved. For future reference, you can do that through the Thread Tools menu.

---

### Post by arm-c on 2012-01-27
Recommend that you take a look at this site for guide if you are US Government and need CAC for work access.

[http://geekyschmidt.com/2011/01/19/your-new-cac-linux-and-you](http://geekyschmidt.com/2011/01/19/your-new-cac-linux-and-you)

NOTE:  Posting for the general community.

---

### Post by redxine on 2012-02-11
I'm afraid I'm not having as much luck.  I've compiled and installed libcackey successfully, however opening firefox with a card in results in an immediate crash.  Crashes when I try the card with it open, and comes back up after I remove the card.

Card is read fine in the pcsc_scan report, and I've loaded the libcackey module in Firefox 8, ubuntu 11.10.  I followed instructions from the GeekySchmidt site above to no avail.

Latest version of libcoolkey yields the same result.

Any suggestions?  My father wishes to completely defenestrate his work at home.

---

### Post by ramirabeau on 2012-03-30
I too am having a terrible time with the installation of cackey.  I have downloaded the file on seperate occasions to eliminate the possibility of a corrupt dload, but I keep getting this error string:

(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 171645 files and directories currently installed.)
Unpacking cackey (from .../cackey_0.6.5-1_amd64.deb) ...
dpkg: error processing /home/myputer/Downloads/cackey_0.6.5-1_amd64.deb (--install):
 unable to create `/usr/lib64/libcackey.so.dpkg-new' (while processing `./usr/lib64/libcackey.so'): No such file or directory
dpkg-deb (subprocess): data: internal gzip write error: Broken pipe
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg-deb (subprocess): failed in write on buffer copy for failed to write to pipe in copy: Broken pipe

If anyone can help, I would greatly appreciate it.

HP dv7-4065; AMD Phenom II N830 x3; 4GB; Ubuntu 11.10

---

### Post by 67comet on 2013-02-16
Old post I know; but I think I have the answer to the failed dpkg install. You need to manually create and empty lib64 in the /usr directory:
sudo mkdir /usr/lib64

Then run it again.

MY problem is that the link everyone posts for cackey seems to be GONE, broken or what ever but I really need to get the cackey .deb file so I can get my access to the Air Force Portal back while on leave.

Any ideas are greatly appreciated,.

---

