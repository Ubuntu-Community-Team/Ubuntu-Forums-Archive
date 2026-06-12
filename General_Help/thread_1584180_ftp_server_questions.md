---
title: "ftp server questions"
date: 2010-09-28
forum: General Help
---

### Post by orlandold on 2010-09-28
I have a ubuntu 9.10 Desktop machine, with a fresh install. 

I need to arrange an ftp server, for said machine to be accessed by two remote applications which will uploading files to it on a constant basis (every 30 seconds I will say). 

The issue is that I am space restricted, therefore I will like to be able to have some sort of functionality/script which allows a check of the folder (for example) size or compare it against a established amount, with the intention that it can automatically start deleting items and at the same time allow new space for the consecutive new files being received. I will like that the oldest files be deleted, keeping always the newest files. 

Is there an ftp server application that works great with Ubuntu, and haves said described functionality? or is there some sort of cron job which can be configured and put that together with a basic ftp service?

thanks for the suggestions.

---

### Post by apjone on 2010-09-29
I do not think an FTP server will have the above functionality. I think you would need to find/write a script to clean up the FTP directory.

---

