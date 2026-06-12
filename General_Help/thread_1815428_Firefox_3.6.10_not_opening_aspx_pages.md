---
title: "Firefox 3.6.10 not opening aspx pages"
date: 2011-07-31
forum: General Help
---

### Post by tech291083 on 2011-07-31
Hi,

I have Firefox version 3.6.10 installed on Ubuntu 10.10 but it for some reason does not open aspx web pages/sites. Can you please help? Thanks...

---

### Post by momist on 2011-11-23
We're now onto Firefox 8.0, and this problem has arisen again.  Just one or two sites using aspx simply result in a dialogue asking what I want the system to do, and offering "choose an application to open this file".  The solution is Chrome.:(

---

### Post by pretty_whistle on 2011-11-23
> **momist said:**
> We're now onto Firefox 8.0, and this problem has arisen again.  Just one or two sites using aspx simply result in a dialogue asking what I want the system to do, and offering "choose an application to open this file".  The solution is Chrome.:(
I had a problem with Chrome where it wouldn't display a webpage's template.  It kept doing this repeatedly.  Worse yet if the page in question had a left or right navigation bar it failed to display it as well.

Didn't always happen and was randomly doing this.

So I dumped off Chrome because of this.  Chromium did it too.

---

### Post by Serpher on 2011-11-23
That's odd since the data received from an ASPX file would be the same as any HTML file unless ASPX has some sort of special garbage it does. Perhaps choose to open it by Firefox with default? From what I know it's sounds just like a file extension issue.

---

### Post by pretty_whistle on 2011-11-23
I have Firefox 8 and can open aspx pages fine-just tested this one:

[http://clerk.house.gov/floorsummary/floor.aspx](http://clerk.house.gov/floorsummary/floor.aspx)

---

### Post by pretty_whistle on 2011-11-23
I also opened this Microsoft page ok:

[http://www.microsoft.com/security/default.aspx](http://www.microsoft.com/security/default.aspx)

Maybe it's the site that's having a problem.

---

### Post by Aleksiy on 2011-11-24
I have the same problem in Firefox 8 - it does not open [http://www.crutchfield.com/](http://www.crutchfield.com/)

---

### Post by WorMzy on 2011-11-24
Works for me.

Try clearing your browser's cache (Ctrl+Shift+Del).

---

### Post by Aleksiy on 2011-11-24
I cleared everything, But still not working

---

### Post by WorMzy on 2011-11-24
Try visiting [http://www.crutchfield.com/S-Sr8sMX6yAbq/](http://www.crutchfield.com/S-Sr8sMX6yAbq/)

Does it work on other browsers?

Are you behind a router that might be caching/interfering with the page?

---

### Post by Benchrest on 2011-11-30
[http://www.crutchfield.com/S-Sr8sMX6yAbq/](http://www.crutchfield.com/S-Sr8sMX6yAbq/)
[http://www.hy-vee.com](http://www.hy-vee.com)
[http://m.briefing.com](http://m.briefing.com)

are three sites I cannot open since installing 8.0 of firefox.

I get the message box:

You have chosen to open

which is a: application/vnd.wap.xhtml+xml(29.8 KB)
from: [http://m.brifing.com](http://m.brifing.com)
What should firefox do with this file?


I have cleared cache with no success.

---

### Post by Benchrest on 2011-11-30
I'm not sure, but I believe this has something todo with the web site thinking we are using a mobile browser and sending invalid web page to us. I installed the XHTML Mobile profile extension to Firefox and get a different error message. Don't understand enough to go any further.

---

### Post by Benchrest on 2011-11-30
found a problem reported that the browser is sending its identification to the web site with the word "ubuntu" included which is confusing the web site. It was suggested to install  "user agent" extension as a workaround. 

The User Agent string FireFox sends when connecting to pix.ie changed has changed from this:

Mozilla/5.0 (X11; Linux x86_64; rv:7.0.1) Gecko/20100101 Firefox/7.0.1

to this:

Mozilla/5.0 (Ubuntu; X11; Linux x86_64; rv:8.0) Gecko/20100101 Firefox/8.0

The addition of "Ubuntu;" seems to have caused an issue with a 3rd party component we use. We will hopefully have an update in the next day or so to fix the issue.

In the meantime, using the User Agent Switcher FireFox addon to "pretend" to be an older browser will fix the issue. 

I set mine to IE8 and can view my web sites. Don't know yet if it might cause other problems.

---

### Post by WorMzy on 2011-11-30
That would explain why it doesn't affect me: I don't use Ubuntu, so my useragent doesn't have that extra value.

---

