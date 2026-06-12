---
title: "OTRS and Ubuntu:  Cron POP3"
date: 2009-12-13
forum: General Help
---

### Post by tooCanad on 2009-12-13
After messing around for a prolonged period trying to get OTRS to poll a pop3 server, I finally got it to work.

There are issues with the way OTRS installs on a Debian system using the the package manager.

The documentation is not written for Debian systems. There is a Debian guide but I found it easier simply to install the deal from source following the documentation.

Getting OTRS up and running using the package manger works fine. Install mySql, then install OTRS.  It works out of the box.  However, trying to poll a pop3 server runs into issues around the user permissions, OTRS wants everthing to run on the user OTRS. Debian systems wants things to run on the www-data user / group. 

I struggled trying to get it to go and eventually gave up, and followed the docs on compiling from source. Everthing works now and I can poll my pop3 server just fine.

---

