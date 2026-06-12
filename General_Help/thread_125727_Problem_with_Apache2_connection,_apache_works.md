---
title: "Problem with Apache2 connection, apache works"
date: 2006-02-04
forum: General Help
---

### Post by michaelbg on 2006-02-04
I've been struggling all afternoon with apache/php. The mysql seems to work ok though.

I follow the ubuntuguide install
sudo apt-get install apache2

no problem. However, [http://localhost](http://localhost) doesn't work, refuses connection.
I installed apache and it works fine (ie. [http://localhost](http://localhost) gives me the placeholder).  However, with apache (not apache2), I don't know how to install the php (as per [https://wiki.ubuntu.com/ApacheMySQLPHP)](https://wiki.ubuntu.com/ApacheMySQLPHP)). 

BTW, I notice that when I start or restart Apache, get a message (ie. Restarting apache.) but with Apache2 I get nothing. Just the prompt returns.

I am running 5.10
with
Linux version 2.6.12-10-amd64-k8 (buildd@crested) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Jan 16 17:23:13 UTC 2006

thanks,
Michael


UPDATE: Forget it.
so it turns out that apache2 doesn't give any messages when it works. 
now it seems to work ok.
just using the regular /etc/init.d/start and stop and it works fine.
So now I'll be struggling with the PHP. There seem to be many many posts on how to fix the saving rather than executing php files.
Thanks anyways.

---

