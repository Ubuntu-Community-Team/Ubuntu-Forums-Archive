---
title: "subversion for Google Code"
date: 2010-12-19
forum: General Help
---

### Post by johnyjj2 on 2010-12-19
Hello,

I need to download project from Google Code at my Ubuntu 9.10 operating system. I have installed subversion but rapidsvn cannot download the project. I write in RapidSVN -> Repository -> Import

> Repository URL: [http://name-of-the-project.googlecode.com/](http://name-of-the-project.googlecode.com/)
Path: /home/mainaccount/projekt

Unfortunately, it says:

>  Execute: Import
Error: Error while performing action: Server sent unexpected return value (405 Method Not Allowed) in response to MKACTIVITY request for '/svn/!svn/act/e7e8317c-85a6-434c-afad-a50015910b15'
Ready

I have found that:

> "Hey folks, I hate to beat a dead horse here, but the easiest way for us to help on these problems is to look at the *complete* request and response from the standard svn client"

And this is what causes the problem because I'm unable to create the proper, full line capable of doing that for Google Code. May somebody help me, please?

Regards!

---

