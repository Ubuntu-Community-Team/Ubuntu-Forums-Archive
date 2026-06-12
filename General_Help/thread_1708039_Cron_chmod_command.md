---
title: "Cron chmod command"
date: 2011-03-16
forum: General Help
---

### Post by bigg2 on 2011-03-16
Hi

What i need to do is.... chmod the directory /data/ and all files and folders inside to 777 every hour but keeping the same user and group.

What would i need to put into "Command" and "Input to command"

Thanks 

(I have attached screen shots to help explain what i am going on about)

---

### Post by HermanAB on 2011-03-16
Howdy,

Make a script like this:
#! /bin/bash
/bin/chmod -R 777 /data/*

Make it executable and drop it into the directory /etc/cron.hourly

---

