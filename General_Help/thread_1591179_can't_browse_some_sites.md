---
title: "can't browse some sites"
date: 2010-10-08
forum: General Help
---

### Post by Chethan S on 2010-10-08
I use lucid with Firefox 4.0 beta 6 for all my browsing requirements. I have windows xp running in the same system. My problem is i am not able to browse some sites like [http://earthexplorer.usgs.gov](http://earthexplorer.usgs.gov) and WordPress blogs in lucid. Same sites open without any issues in my windows install. I tried changing my dns servers from automatic to Google dns servers, opendns servers and so on. Still the problem persists.

In my windows installation I have configured port forwarding and set up manual ip addresses but have not done it under ubuntu. In fact its only recently I started facing such weird issues.

---

### Post by dmillerct on 2010-10-08
> **Chethan S said:**
> I use lucid with Firefox 4.0 beta 6 for all my browsing requirements. I have windows xp running in the same system. My problem is i am not able to browse some sites like [http://earthexplorer.usgs.gov](http://earthexplorer.usgs.gov) and WordPress blogs in lucid. Same sites open without any issues in my windows install. I tried changing my dns servers from automatic to Google dns servers, opendns servers and so on. Still the problem persists.

In my windows installation I have configured port forwarding and set up manual ip addresses but have not done it under ubuntu. In fact its only recently I started facing such weird issues.

What is the IP scheme you are using? You can always check if DNS is functioning properly by typing:
```
nslookup yahoo.com
```
where yahoo.com is the URL of the site you are having an issue with.

---

### Post by andrewthomas on 2010-10-08
> **Chethan S said:**
> I use lucid with Firefox 4.0 beta 6 for all my browsing requirements. I have windows xp running in the same system. My problem is i am not able to browse some sites like [http://earthexplorer.usgs.gov](http://earthexplorer.usgs.gov) and WordPress blogs in lucid. Same sites open without any issues in my windows install. I tried changing my dns servers from automatic to Google dns servers, opendns servers and so on. Still the problem persists.

In my windows installation I have configured port forwarding and set up manual ip addresses but have not done it under ubuntu. In fact its only recently I started facing such weird issues.
 [http://earthexplorer.usgs.gov]("http://earthexplorer.usgs.gov/")  this site requires some google earth 

[http://packages.ubuntu.com/lucid/googleearth-package](http://packages.ubuntu.com/lucid/googleearth-package)

---

### Post by corcomp84 on 2010-10-08
what is the error code, or a description of whats happening.. I know that sometimes I have a problem when trying to log into certain sites.. but it doesn't happen all the time.. it has something to do with the certificate.. just a guess..

---

### Post by Chethan S on 2010-10-09
> **andrewthomas said:**
> [http://earthexplorer.usgs.gov]("http://earthexplorer.usgs.gov/")  this site requires some google earth 

[http://packages.ubuntu.com/lucid/googleearth-package](http://packages.ubuntu.com/lucid/googleearth-package)

I have tried after installing googleearth-package, still the problem persists.

> **corcomp84 said:**
> what is the error code, or a description of whats happening.. I know that sometimes I have a problem when trying to log into certain sites.. but it doesn't happen all the time.. it has something to do with the certificate.. just a guess..

When I type in the URL the progress bar at the bottom either loads 50% and thereafter nothing happens for a long time. Later "Server not found" message gets displayed.

> **dmillerct said:**
> What is the IP scheme you are using? You can always check if DNS is functioning properly by typing:
```
nslookup yahoo.com
```where yahoo.com is the URL of the site you are having an issue with.

When I used nslookup earthexplorer.usgs.gov, I get the following output:
> Server:        218.248.245.1
Address:    218.248.245.1#53

Non-authoritative answer:
earthexplorer.usgs.gov    canonical name = edcsns17.cr.usgs.gov.
Name:    edcsns17.cr.usgs.gov
Address: 152.61.128.70

Its not only earthexplorer.usgs.gov but its the same case for linuxtoday.com as well.

---

### Post by lovinglinux on 2010-10-09
Have you tried to disable ipv6? See the fifth item on [this list]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html").

---

### Post by Chethan S on 2010-10-09
Unfortunately nothing is happening. Its the same. Progress bar loading 50% and making me wait forever.

---

### Post by sendblink23 on 2010-10-09
> **Chethan S said:**
> Unfortunately nothing is happening. Its the same. Progress bar loading 50% and making me wait forever.

Did you try installing Chromium and testing to see if the website opens through there.. it won't hurt having an extra faster web browser to play with

---

### Post by Chethan S on 2010-10-09
I have done that. I run the latest version of google-chrome-stable and flock-browser. Its the same case everywhere. The only way I have found out is using freeproxyserver.net which allows me to browse the sites without any issues.

---

### Post by sendblink23 on 2010-10-09
> **Chethan S said:**
> I have done that. I run the latest version of google-chrome-stable and flock-browser. Its the same case everywhere. The only way I have found out is using freeproxyserver.net which allows me to browse the sites without any issues.

wow! now that sure is very odd then... needing a proxy server to open it when you have made changes to firefox & even tested other browsers and they wouldn't work with the site

isn't there an option inside firefox to mess with proxy ?
Open up Firefox > Edit > Preferences > Advanced > network > Settings

Then mess with the proxy there
---  hehe actually forget about it, I don't know anything about proxy - so I'm certain that won't help on anything.. keep using the free proxy site then

---

### Post by Chethan S on 2010-10-09
I got the problem solved this way:

[LIST=1]
[*]I tried changing the MTU value to 1492 as suggested in many web forums but it yielded me no results.
[*]I even disabled Network Manager and used WiCD as some forums suggested. However this gave me no advantage.
[*]Finally I used "sudo pppoeconf" and reconfigured everything. In fact I used the default options like connecting at startup, the default MTU value suggested and so on. Now my internet works like a charm. I have access to all the sites which I didn't have access to erstwhile since many days. I really missed linuxtoday.com.
[/LIST]
I would like to conclude that at least in my case it was the buggy network manager which causes lot of problems. Regarding wicd I have no idea but as I could not configure pppoe connection using username and password, I had to abandon that.

Hope this helps!

---

### Post by kranthi.doss on 2011-06-14
I  installed ubuntu 11.04 yesterday and was stuck up with the same reason.

Thank you chetan. Your updates were helpful. Everything works fine now.

---

