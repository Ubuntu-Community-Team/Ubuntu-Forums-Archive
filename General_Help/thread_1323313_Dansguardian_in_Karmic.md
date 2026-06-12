---
title: "Dansguardian in Karmic"
date: 2009-11-11
forum: General Help
---

### Post by Istonian on 2009-11-11
I have heard of some people having issues with Dansguardian in Karmic. I searched around but I was wondering what is the best way to install Dansguardian on Karmic? 

I have a cable modem connected to a wireless router. My desktop is hooked up to the wireless router directly.

---

### Post by fluffman86 on 2009-11-11
Not sure what you want to use it for, but if it's for porn filtering I recommend getting the dansgaurdian package from Ubuntu CE:
[http://ubuntuce.com/convert.htm](http://ubuntuce.com/convert.htm)

Follow the directions there until you get to the last line.  Leave out the "sudo apt-get install ubuntu-ce" part, unless you want to install ALL the ce packages.

Then, after updating, just do:
sudo apt-get install dansgaurdian-gui

And you'll have really simple web filtering.  I just did it today and didn't have any trouble out of it.

---

### Post by kennedyjch on 2009-11-11
I too am having problems. I had tinyproxy and dansguardian installed and working properly under 9.04. I upgraded to 9.10 and many sites display as blank pages. I verified that if I go through tinyproxy alone, the sites display properly. For example, navigate to [www.kidrex.org](www.kidrex.org) and perform a search. Under 9.10 and dansguardian, no results of the search are displayed.

I reinstalled a fresh 9.10, tinyproxy and dansguardian and replicated the same problem. The install was from the CD (9.10); I then upgraded to get all the patches/fixes; then installed tinyproxy and dansguardian using Synaptic package manager (gui).

I use this software to let my 6 year old access the web in a controlled and monitored manner. And it seemed to work well under 9.04. 

Any clues how to get it working under 9.10?

---

### Post by kennedyjch on 2009-11-11
I have found a "workaround" but not a solution to the problem. On the dansguardian sourceforge page under bugs it reads:

> Version 2.10.1.1 delivers an empty page from some sites (e.g.,
[http://www.adobe.com/downloads/](http://www.adobe.com/downloads/)). I'm using it with tinyproxy on Ubuntu
9.04. Using packet captures I've confirmed that DG is downloading a full
page (about 48K) from the above URL, but only the headers are returned to
the browser. The DG access.log shows a zero-size page retrieval, but no
deny or error message . I confirmed this result by connecting to the DG
port with netcat and sending GET [http://www.adobe.com/downloads/](http://www.adobe.com/downloads/) HTTP/1.1
by hand -- packet capture shows DG retrieves the entire page, but only the
headers were retrieved. If I send GET [http://www.adobe.com/downloads/](http://www.adobe.com/downloads/)
HTTP/1.0 the entire content is returned. After reading problem description
in bug ID 1452799 I tried listing [www.adobe.com](www.adobe.com) in the exceptionsitelist.
When I do this, DG downloads the page normally.

So I was able to put the kidrex.org on the exceptionsitelist and at least get searches to work. However, some pages are still blocked, as per the above.

---

### Post by Istonian on 2009-11-13
I really need to find a fix. I have the same error.

---

### Post by kennedyjch on 2011-10-15
Well, did some digging around and low and behold the problem seems to be in the tinyproxy-dansguardian interface. I gave the boot to tinyproxy and replaced it with squid and guess what??? It now works and (to date) no blank web pages...

So for the moment I treat the problem as resolved.

---

### Post by oldos2er on 2011-10-15
Closed, necromancy.

---

