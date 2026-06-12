---
title: "Problems install Firefox Add-on in Ubuntu 10.10"
date: 2010-10-04
forum: General Help
---

### Post by aimwin on 2010-10-04
The Problems solved.
I found that it was Internet connection, 
"may be" wrong DNS setting in the router.
(I cannot change setting in the router to proof this Theory yet.
I will update later, when I have permission to change the router setting)

The issue is ok, 
it work perfect, 
when I connected to another internet connection,
(in my house).
It load all the Addon with no hassle.
----------------------------

With the same problematic Internet connection.

[COLOR="Red"]I found that Firefox cannot connect to any website.
except [www.google.com](www.google.com), 

but in another computer, I cannot browse any website.
(Though the using of the same Internet connection,
all MS windows booted from the same computers,
Firefox has no problems in access Internet,
only in UBUNTU booted Firefox.)

But Google Chrome can in both computers
And any web page that Google Chrome can connect,
Firefox can connect after that.[/COLOR]

So if you have the same issues and cannot change the internet connection,
nor cannot access the router to change DNS settings.

Try to use Google Chrome instead,
 to see if you can browse the Internet.

(I changed the settings of Network in Firefox 
from System Proxy to no proxy and other proxy settings but all not working,
Google Chrome Network setting is Direct INternet Connection)

My brother help identify the problems, it is from DNS setting in the router.
We can access the website using [http://126.###.XXX.###](http://126.###.XXX.###).
So if you Firefox cannot access [www.yourwhateverwebsite.com](www.yourwhateverwebsite.com),
try [http://123.456.789.123](http://123.456.789.123), 
(put the real ip address of any website, not my imaginary number as shown)

if it can access,

 then DNS setting in the router may be wrong.

And TRY Google Chrome,

 I found it smarter to get around this issue,
and save your time or your life if you need to get that email now.

So the conclusion is,
      if the router has got the wrong DNS,
      use Google Chrome instead of Firefox.
And hope, you will get the same result as mine.
Good luck

-------------------below was the original post--------------------

I have fresh installed ubuntu 10.10 release candidate 5 October 2010
I have many failed installation of Firefox Add-on as in attached file.

I boot up to the old ubuntu 10.04 in another partition.
Remove all Firefox Add-ons. Add all the preferred Add-ons, no hickup at all.
And have no issues.

Back to ubuntu 10.10 delete Firefox defualt profile.
So it look clean and start install Add-ons.
The same issues again.
Some Add-ons will not install.
It is random.
Many earlier reboots in Ubuntu 10.10 result in the same issue.

Any one has the same problems.
I am checking up before report as bugs in Ubuntu 10.10

---

### Post by lovinglinux on 2010-10-05
Try to save the add-on instead of installing it. Instead of clicking the "Add to Firefox" button, right-click on it and select "Save Link As", then drag the saved xpi file to Firefox to install it.

---

### Post by aimwin on 2010-10-14
> **lovinglinux said:**
> Try to save the add-on instead of installing it. Instead of clicking the "Add to Firefox" button, right-click on it and select "Save Link As", then drag the saved xpi file to Firefox to install it.

Thanks you LovingLinux, I solve the problems,
pleas see the modified original post.

Can you comment on my experience and conclusion, please?

---

### Post by lovinglinux on 2010-10-15
> **aimwin said:**
> Thanks you LovingLinux, I solve the problems,
pleas see the modified original post.

Can you comment on my experience and conclusion, please?

Have you tried to disable ipv6? See the fifth item on [this list]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html"). Most likely that it will solve the problem, since you can access the sites via IP.

On a side note, Mozilla site is under heave changes lately, so such kind of issues are not uncommon. Nevertheless, in your case is probably an ipv6 issue.

---

### Post by aimwin on 2010-10-16
> **lovinglinux said:**
> Have you tried to disable ipv6? See the fifth item on [this list]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html"). Most likely that it will solve the problem, since you can access the sites via IP.

On a side note, Mozilla site is under heave changes lately, so such kind of issues are not uncommon. Nevertheless, in your case is probably an ipv6 issue.

I check and found by default ipv6 is enable. I will try your suggestion.
Which may be the problems.

---

