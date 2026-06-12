---
title: "Ubuntu Apache"
date: 2012-04-01
forum: General Help
---

### Post by AMcIntyre2012 on 2012-04-01
Hello

I am relatively new to Ubuntu Apache and I am struggling to figure out the basic set-up of hosting a domain name at home with Apache2. I understand that you have to change your IP from dynamic to a static IP Address but I am not sure how you achieve that step.

I am looking for some assistance on this on how to enable self signing certificates, make the domain name resolve on the Internet from hosting the website on the web server, enabling protected directories and the basic commands of accessing the directory where the website files can be uploaded and available on the World Wide Web.

Please forgive me if I have posted this in the wrong section of the forums.

Thank you

---

### Post by jaybutts on 2012-04-01
Your asking quite a bit here, someone would need to write a novel to respond to this adequately. This type of format is best used for SPECIFIC questions. The main thing you need to do first is familiarize yourself with apache on linux. Read the apache documentation at apache.org, start by configuring your apache from httpd.conf..

Better yet...Google for ubuntu LAMP tutorial

---

### Post by AMcIntyre2012 on 2012-04-01
If you could tell me on how to set up the domain name and get it to resolve I could get it from there.

---

### Post by dragonfly41 on 2012-04-01
re: dynamic IP address .. home server .. this link should help

[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

setup an account with say dyndns.com .. there are others such as zoneedit

make sure that your Internet provider allows access .. you might need to run on port 8080 instead of 80

---

