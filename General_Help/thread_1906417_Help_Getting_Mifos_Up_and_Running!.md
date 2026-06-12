---
title: "Help Getting Mifos Up and Running!"
date: 2012-01-09
forum: General Help
---

### Post by frankjath on 2012-01-09
Hi I have spent the past couple of days pulling my hair out trying to get Mifos installed and running on my Ubuntu server. I have followed the instructions from [here]("http://mifosforge.jira.com/wiki/display/MIFOS/Ubuntu+WAR+Install"). I have LAMP,  Jetty7, and Maven2 installed and running I have also downloaded and extracted Mifos to the root of the server. I have moved the mifos.war file and extracted it to "jetty7/webapps" like the instructions says. I have also set up the databases with phpmyadmin.

When I vist my ip in a browser apache is running because it says 

"It works!

This is the default web page for this server.

The web server software is running but no content has been added, yet."

However when I vist "myip/mifos" it doesn't show up I get

"Not Found

The requested URL /mifos was not found on this server.

Apache/2.2.14 (Ubuntu) Server at 50.56.209.57 Port 80"

Help would be very much appreciated as its very importent that I get this up and running with in the next few days.

---

### Post by SlugSlug on 2012-01-09
> **frankjath said:**
> 

However when I vist "myip/mifos" it doesn't show up I get


looking at the instructions it should be [http://myip:8080/mifos](http://myip:8080/mifos)

---

### Post by frankjath on 2012-01-09
I tried that and it said "Oops Google Chrome can not connect to myip."

---

### Post by SlugSlug on 2012-01-09
have you opened port 8080 in your firewall / router?

can you connect locally on the box running apache [http://localhost:8080/mifos](http://localhost:8080/mifos)

---

### Post by frankjath on 2012-01-09
My server is a VPS cloud server on rackspace and I haven't set up any firewalls. If I am not mistaken isn't the firewall off by default? If I need to open a port how would I go about it?

---

