---
title: "Ubuntu 10.04 Firefox cannot browse Internet but Google Chrome Can"
date: 2010-10-15
forum: General Help
---

### Post by aimwin on 2010-10-15
[COLOR="Red"]
Problems Solved, using instruction from

[http://support.mozilla.com/en-US/kb/Firefox%20cannot%20load%20websites%20but%20other%20programs%20can#w_ipv6](http://support.mozilla.com/en-US/kb/Firefox%20cannot%20load%20websites%20but%20other%20programs%20can#w_ipv6)
[/COLOR]
the following instruction copy from the above link.
------------------
IPv6
Firefox supports IPv6 by default,
which may cause connection problems on certain systems. To disable IPv6 in Firefox:

1. In the Location bar, type "about:config" and press Enter.
2. Firefox should now show ==> The about:config "This might void your warranty!" warning page may appear.
   Click I'll be careful, I promise!, to continue to the about:config page.

3. In the Filter field, type network.dns.disableIPv6.

4. In the list of preferences, 
   double-click network.dns.disableIPv6 to set its value to true.

Then try to refresh the page you cannot access, if you still cannot access,
then it is not this problem.
For me it works immediately after set to "true"
=====================================================

OS -- is Ubuntu 10.04 and Edubuntu 10.04
On Dell Vostro 3700, Dell Inspiron 4010, IBM Thinkpad (cannot remember version) and OEM Austek Notebook.

[COLOR="Red"]Wireless and router (my dad's house) are both Dlink.[/COLOR]

Wireless -- using its own broadcom and external WG111v2.
I used WG111v2 to install update for Dell notebooks' broadcom and nvedia drivers with all notebooks with no issues.
Then I remove WG111v2 and let Dells use Broadcom.
IBM thinkpad use WG111v2 as wireless adapter.
I have no time to try Ubuntu older versions on these computers.

But no issue on my old Asus OEM Notebook ?? don't know why?
----> edit 14 JAN 2011, after Brand New installation of my Ubuntu 10.10 and 10.04 (in the separated partition),
Firfox did not work any longer only Chrome ---------
------------------------------------

I found that Firefox cannot browse any website.
except [www.google.com](www.google.com), for one computer, IBM.

but in Dell computers, I cannot browse any website.

([COLOR="Red"]Though the using of the same Internet connection,
all MS windows booted from the same computers,
Firefox has no problems in access Internet,
only in UBUNTU booted Firefox[/COLOR].)

[COLOR="Red"]But Google Chrome can in all computers (and all OS).
And any web pages that Google Chrome can connect,
Firefox can connect only to those web pages after that, immediately.
[/COLOR]
So if you have the same issues and cannot change the internet connection,
nor cannot access the router to change DNS settings.

Try to use Google Chrome instead,
to see if you can browse the Internet.

(I changed the settings of Network in Firefox
from System Proxy to no proxy and other proxy settings but all not working,
Google Chrome Network setting is Direct INternet Connection)

My brother help identify the problems, it is from DNS setting in the router.
we cannot change the settings.

Firefox in IBM Thinkpad and Dell 4010 work fine in my house,
which has different router and wireless access point.
I took them back to my dad's house, it won't work there.

So if you Firefox cannot access [www.yourwhateverwebsite.com](www.yourwhateverwebsite.com),
try [http://123.456.789.123](http://123.456.789.123),
(put the real ip address of any website, not my imaginary number as shown)

if it can access,

then DNS setting in the router may be wrong.

And TRY Google Chrome,

I found it smarter to get around this issue,
and save your time or your life if you need to get that email now.
---------------------------------------
How ever My notebook, Asus Oem notebook,
Intel wireless internal PCI,
have no issue what so ever using 10.04 and older versions,
in my dad's house,
which create problems for those 3 other fresh installed ubuntu 10.04 computers.
So I don't know where to blame.
--------------------------------

So the conclusion, for my Environment, is,
the router may has the wrong DNS,

You may use Google Chrome instead of Firefox.

And hope, you will get the same result as mine.
Good luck
-----------------------------------------

I am looking to try
Firefox cannot load websites but other programs can......
[http://support.mozilla.com/en-US/kb/Firefox%20cannot%20load%20websites%20but%20other%20programs%20can](http://support.mozilla.com/en-US/kb/Firefox%20cannot%20load%20websites%20but%20other%20programs%20can)

and the 5th topic from the top.
# Firefox can&#8217;t connect to any sites, but other browsers work
# Firefox can connect to sites only using the IP number
[http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html)

But I won't be able to try that in the next few weeks,
I will update the result.
==================================================
So at present my dad's Dell Vostro 3700, 
can only use Google Chrome in Edubuntu 10.04 to browse internet.

And he wants Firefox.
So he has to use windows 7, which Firefox perform without flaws.
Thanks in Advance for all the Gurus to identify the problems.

---

### Post by DeMus on 2010-10-15
You could rename the hidden /mozilla folder in your home directory. After that start Firefox again and see what it does.
What you do is removing your profile with all the info which is stored on disk when using the program. You will now start over with a new profile and it could well be that it will work now.
Success.

---

### Post by ubudog on 2010-10-15
> **DeMus said:**
> You could rename the hidden /mozilla folder in your home directory. After that start Firefox again and see what it does.
What you do is removing your profile with all the info which is stored on disk when using the program. You will now start over with a new profile and it could well be that it will work now.
Success.

This always works when this happens to me.

---

### Post by aimwin on 2010-10-15
> **DeMus said:**
> You could rename the hidden /mozilla folder in your home directory. After that start Firefox again and see what it does.
What you do is removing your profile with all the info which is stored on disk when using the program. You will now start over with a new profile and it could well be that it will work now.
Success.

Thanks DeMus, and ubudog

I did that earlier, before I start this Thread, it was not working.

I am looking to try
Firefox cannot load websites but other programs can......
[http://support.mozilla.com/en-US/kb/...programs%20can](http://support.mozilla.com/en-US/kb/...programs%20can)

and the 5th topic from the top.
# Firefox can&#8217;t connect to any sites, but other browsers work
# Firefox can connect to sites only using the IP number
[http://firefox-tutorials.blogspot.co...solutions.html](http://firefox-tutorials.blogspot.co...solutions.html)

But I won't be able to try that in the next few weeks,
I will update the result.

---

### Post by ubudog on 2010-10-15
Ok, cool.

---

### Post by deanom on 2010-11-19
Hi All
From a complete newbie.
I found this thread before posting about the same problem. After a new full install of 10.10 on an old laptop, I couldn't browse any websites in Firefox. I was able to download Chromium, and use that instantly. However I was able to use Firefox on the same laptop, when connected to a different network.  
Logically it would seem to be a router problem. 
It would be feasible to just stick to Chromium, but that seems to defeat the point of having more control.

Thanks

Deano

---

### Post by deanom on 2010-11-19
> **deanom said:**
> Hi All
From a complete newbie.
I found this thread before posting about the same problem. After a new full install of 10.10 on an old laptop, I couldn't browse any websites in Firefox. I was able to download Chromium, and use that instantly. However I was able to use Firefox on the same laptop, when connected to a different network.  
Logically it would seem to be a router problem. 
It would be feasible to just stick to Chromium, but that seems to defeat the point of having more control.

Thanks

Deano
Oops
Should have mentioned that Router is D-Link G624T
In case it is relevant
Cheers
Deano

---

### Post by ubudog on 2010-11-19
Deanom - Did you also try removing the .mozilla directory?  Make sure you have it backed up on say a flash drive first.

---

### Post by aimwin on 2011-01-14
> **DeMus said:**
> You could rename the hidden /mozilla folder in your home directory. After that start Firefox again and see what it does.
What you do is removing your profile with all the info which is stored on disk when using the program. You will now start over with a new profile and it could well be that it will work now.
Success.

I am back at the trouble spot.
I did that,
delete folder .mozilla in the home directory,
and it is not working.

Though .mozilla is created again after I restart the Firefox.

I use the same notebook in other places, no problem at all.

I have to use Google Chrome to write this post.

---

