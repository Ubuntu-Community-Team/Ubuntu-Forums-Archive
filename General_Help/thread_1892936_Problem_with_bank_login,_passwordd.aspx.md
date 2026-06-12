---
title: "Problem with bank login, passwordd.aspx"
date: 2011-12-09
forum: General Help
---

### Post by gseward on 2011-12-09
This just started two days ago, and happens on both my desktop,(Ub11.10, Firefox 8.0) and my laptop (Ub11.10, Firefox 8.0).
When I login to my credit union I enter my user id and click Go and I should get a new page where I can enter my password, instead I get a dialog "You have chosen to open Password.aspx What should Firefox do with this file?  Open with [Browse], Save file.
This login worked fine on both computers prior to today and still works fine on my Windows XP computer. Not sure if the bank changed something or if an update changed something on my linux computers. I am pretty sure it is the same page, as I go there with a bookmark.
To attach password.aspx I had to rename it as a .txt file.
Any help would be appreciated, I am at a complete loss where to go with this, and the bank doesn't want to deal with Linux problems.

---

### Post by kreemoweet on 2011-12-09
This is a bank website server problem, got nothing to do with Linux. They should not be
sending you .aspx files. If you need proof, you can capture the http headers served by
activating the logging facility in Firefox, using some packet sniffer application such as Wireshark,
or installing a FireFox extension which captures http headers. I can't say I'm familiar with any
specific Linux Firefox extensions that do that, but I know there are several for the Windows
version of Firefox.

---

### Post by deserthowler on 2011-12-09
I have the same problem with one of my bank accounts.  My quick and easy fix is to use chromium.  

It seems to happen on this site every time I update Firefox.  I think they recognize about 2 versions behind.

Earl

---

### Post by lovinglinux on 2011-12-14
> **deserthowler said:**
> I have the same problem with one of my bank accounts.  My quick and easy fix is to use chromium.  

It seems to happen on this site every time I update Firefox.  I think they recognize about 2 versions behind.

Earl

Then using [User Agent Switcher](https://addons.mozilla.org/en-US/firefox/addon/59/) should probably solve the problem.

---

