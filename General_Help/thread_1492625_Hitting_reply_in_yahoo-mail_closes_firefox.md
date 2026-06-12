---
title: "Hitting reply in yahoo-mail closes firefox"
date: 2010-05-24
forum: General Help
---

### Post by rinrada on 2010-05-24
Just upgraded my Asus netbook to Lucid Lynx and found this very strange bug / problem.

I can open yahoo mail and read content, delete mail etc but when I hit Reply Firefox closes. The Reply page initially opens correctly but then FF immediately crashes. 

I tried reinstalling Firefox - no luck there. When I went to the yahoo "More options" to see if there was some security setting - it also closed. Then when I searched Ubuntu Forums  and clicked on the thread.

"Gmail/Yahoo does not work in Firefox/Chrome in 10.04"

it closed again (I am currently using a different computer with Ubuntu 9.04). Clicking on some, but not all, google hits also causes FF to close after initially opening the page.

I checked the Firefox settings but did not notice anything unusual - then again this idiosyncratic behaviour is difficult (for me) to understand.

---

### Post by tgalati4 on 2010-05-25
Open a terminal and run:

firefox --debug

Then run yahoo and post the output after firefox crashes.  Might have something to do with Yahoo and MS merging.

---

### Post by rinrada on 2010-05-25
Nothing very useful, it seems. When I clicked on this thread ff also closed. Now I am using my Desktop. When I closed terminal, I got the "Process still running.." warning but nothing was written to the terminal following the crash.


sh /usr/lib/firefox-3.6.3/run-mozilla.sh /usr/bin/gdb /usr/lib/firefox-3.6.3/firefox-bin -x /tmp/mozargs.hjC7iG
GNU gdb (GDB) 7.1-ubuntu
Copyright (C) 2010 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i486-linux-gnu".
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>...
Reading symbols from /usr/lib/firefox-3.6.3/firefox-bin...(no debugging symbols found)...done.
(gdb)

Now I am leaving it to run, in case I just need to wait longer.

---

### Post by tgalati4 on 2010-05-27
I'm sorry, you need to type "run" at the (gdb) prompt to continue execution of firefox inside the debugger.  Type "quit" when you want to exit.

---

### Post by caradeporra on 2010-05-27
I am having what i believe is the same issue, it has nothing to do with yahoo mail.  I believe it has something to do with flash and something called no-script.

If you google "firefox 10.04 bryce harrington" you can come across what is supposedly a fix for this, however this did not relieve my issue.  The issue remains that I can open firefox, go to google and it's ok.  Gmail, Youtube, and many other websites immediately close firefox - no error messages or anything.  I started firefox in safe mode with no add-ons and deleted all extensions, pages, user settings etc. and it still happens.

This is a MAJOR issue, because if I can't run firefox I am in trouble - I also use opera, but that is because I have, well had, an issue with opening multiple instances of firefox - as in, I could not open more than one instance.  That is another issue for another day, right now I JUST NEED FIREFOX TO FUNCTION!

Any help on this would be greatly appreciated as I have been googling for several days now trying to figure this thing out to no avail.

---

### Post by lovinglinux on 2010-05-27
> **caradeporra said:**
> I am having what i believe is the same issue, it has nothing to do with yahoo mail.  I believe it has something to do with flash and something called no-script.

NoScript is a Firefox extension that prevents untrusted web sites from running scripts. It can block flash content too.

> **caradeporra said:**
> If you google "firefox 10.04 bryce harrington" you can come across what is supposedly a fix for this, however this did not relieve my issue.

Please be careful when following tutorials from random sites. If you followed that tutorial, then you have included a PPA repository to update xorg server from a third-party source. If that didn't fix your problem,  then you should disable that PPA and restore the default xorg.

I read the site that talks about that problem. I have no problems whatsoever with NoScript crashing Firefox and I haven't seen any threads on these forums reporting that behavior. There are threads reporting crashes, but several of them are related to libmoon package (Silverlight). If the user has libmoon installed, then removing it usually fixes the problem. Try that.

> **caradeporra said:**
> This is a MAJOR issue, because if I can't run firefox I am in trouble - I also use opera, but that is because I have, well had, an issue with opening multiple instances of firefox - as in, I could not open more than one instance.

Firefox doesn't allow to open multiple instances. If you click the Firefox launcher while Firefox is already opened, it will open a new window. You can force Firefox to open a new instance by using the command below. Nevertheless, you won't be able to use the same profile already in use. You need to open it with a second profile:

```
firefox -no-remote -P
```

> **caradeporra said:**
> ...right now I JUST NEED FIREFOX TO FUNCTION!

What version of Ubuntu, Firefox and Flash you are running? Is your system 32bit or 64bit?

---

### Post by caradeporra on 2010-05-27
Thanks for that info - could you please show me how to go back to the original xorg.  I have already removed that from the repo.

---

### Post by Smart Viking on 2010-05-27
Hi all.

I used 32 bit Ubuntu before on my desktop and it very often behaved weird, Firefox sometimes just quited and i sometimes got logged out without any error messages. But after a changed to 64 bit i have had none of those problems. I just wanted to add that to say that it somehow fixed it for me to switch to 64 bit. But i don't know if that is the same problem you are having. :)

---

### Post by caradeporra on 2010-05-27
> 
I read the site that talks about that problem. I have no problems whatsoever with NoScript crashing Firefox and I haven't seen any threads on these forums reporting that behavior. There are threads reporting crashes, but several of them are related to libmoon package (Silverlight). If the user has libmoon installed, then removing it usually fixes the problem. Try that.


  You were very correct on this.  I had installed libmoon several months back to see what it was about (needless to say it didn't work), however this issue only begun when I updated to 10.04, as 9.10 had no issues like that.  I would have NEVER discovered that it was libmoon causing that - after uninstalling Firefox is back to it's normal self.  

  Thank you very much.  Now I will begin my google search to rever back the xorg.  thanks again!

---

### Post by lovinglinux on 2010-05-27
> **caradeporra said:**
> Thanks for that info - could you please show me how to go back to the original xorg.  I have already removed that from the repo.

I'm not sure. I followed that tutorial on a Virtual Machine to see what files were changed by that PPA. The files were *xserver-common* and *xserver-xorg-core*. Then I disabled the PPA and tried to re-install the packages, but apt wouldn't allow me to do so.

I guess you will need to wait for a new update, unless someone else knows a solution.

---

### Post by rinrada on 2010-05-30
Sorry. I was off-line for a few days. Thanks for the comments

I do not have the libmoon package installed - so that cannot be the problem. I am not sure how to check whether I am using a 32 or 64 bit, though I assume it is 64.

Below is the printout from the debugging.


(gdb) run
Starting program: /usr/lib/firefox-3.6.3/firefox-bin 
[Thread debugging using libthread_db enabled]
[New Thread 0xb53ffb70 (LWP 1570)]
[New Thread 0xb4bfeb70 (LWP 1571)]
[New Thread 0xb43fdb70 (LWP 1572)]
[New Thread 0xb37ffb70 (LWP 1573)]
[New Thread 0xb2dffb70 (LWP 1574)]
[Thread 0xb2dffb70 (LWP 1574) exited]
[New Thread 0xb2dffb70 (LWP 1575)]
[New Thread 0xb200cb70 (LWP 1576)]
[New Thread 0xb102bb70 (LWP 1577)]
[New Thread 0xb082ab70 (LWP 1578)]
[New Thread 0xb0029b70 (LWP 1579)]
[New Thread 0xaf6ffb70 (LWP 1580)]
[Thread 0xb200cb70 (LWP 1576) exited]
[Thread 0xb102bb70 (LWP 1577) exited]
[Thread 0xb0029b70 (LWP 1579) exited]
[Thread 0xb082ab70 (LWP 1578) exited]
[Thread 0xb2dffb70 (LWP 1575) exited]
[New Thread 0xb200cb70 (LWP 1581)]
[New Thread 0xb102bb70 (LWP 1582)]
[New Thread 0xb0029b70 (LWP 1584)]
[New Thread 0xb082ab70 (LWP 1585)]
[Thread 0xaf6ffb70 (LWP 1580) exited]
[New Thread 0xadaffb70 (LWP 1586)]
[Thread 0xb0029b70 (LWP 1584) exited]
[New Thread 0xaf6ffb70 (LWP 1587)]
[New Thread 0xacfffb70 (LWP 1588)]
[New Thread 0xac7feb70 (LWP 1589)]
[New Thread 0xb0029b70 (LWP 1590)]
[New Thread 0xabbffb70 (LWP 1591)]
[New Thread 0xab3feb70 (LWP 1592)]
[New Thread 0xaabfdb70 (LWP 1593)]
[Thread 0xb0029b70 (LWP 1590) exited]
[Thread 0xabbffb70 (LWP 1591) exited]
[Thread 0xab3feb70 (LWP 1592) exited]
[New Thread 0xb0029b70 (LWP 1594)]
[Thread 0xb0029b70 (LWP 1594) exited]
[New Thread 0xb0029b70 (LWP 1595)]
[New Thread 0xabbffb70 (LWP 1596)]
[New Thread 0xab3feb70 (LWP 1597)]
[New Thread 0xa9affb70 (LWP 1598)]
[Thread 0xb0029b70 (LWP 1595) exited]
[Thread 0xabbffb70 (LWP 1596) exited]
[Thread 0xadaffb70 (LWP 1586) exited]
[Thread 0xa9affb70 (LWP 1598) exited]
[New Thread 0xb0029b70 (LWP 1599)]
[New Thread 0xabbffb70 (LWP 1600)]
[New Thread 0xadaffb70 (LWP 1601)]
[Thread 0xadaffb70 (LWP 1601) exited]
[New Thread 0xadaffb70 (LWP 1602)]
[Thread 0xadaffb70 (LWP 1602) exited]
[New Thread 0xadaffb70 (LWP 1603)]
[Thread 0xadaffb70 (LWP 1603) exited]
[New Thread 0xadaffb70 (LWP 1607)]
[New Thread 0xa9affb70 (LWP 1608)]
[New Thread 0xa20c1b70 (LWP 1609)]
[New Thread 0xa15e6b70 (LWP 1610)]
[Thread 0xa15e6b70 (LWP 1610) exited]
[New Thread 0xa15e6b70 (LWP 1611)]
[Thread 0xa15e6b70 (LWP 1611) exited]
[New Thread 0xa15e6b70 (LWP 1612)]
[Thread 0xa15e6b70 (LWP 1612) exited]

(firefox-bin:1567): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1567): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1567): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1567): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:1567): Gdk-WARNING **: XID collision, trouble ahead

---

