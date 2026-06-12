---
title: "Permissions for website"
date: 2010-01-08
forum: General Help
---

### Post by Norseman on 2010-01-08
Hi all,

I am brand new to Ubuntu so please bear with me. 

I am setting this system up to run as a server so that I can run several websites and a voice comm server from it.

 I installed Ubuntu 9.10 and the install went well.  I then installed lamp using the Terminal and that too went well.  I tested Apache, MySQl, and PhP and they are all functioning properly allowing me to visit my test page.

I am now at a loss on how to set it up so that I can host 4 seperate website from this one server.  From what I have read, the site data needs to be in the /var/www folder.  This folder has permissions set to it that I cannot access.  That is one problem.  The other problem I have is how do I configure lamp/ubuntu to have 4 seperate and distinct url addresses?  Will the 4 seperate programs all reside in the www folder?  If not then where?

---

### Post by bodhi.zazen on 2010-01-08
Use "virtual hosts"

You can do it name based or ip based, name based is more common.

[https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts](https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts)

Personally I do it via

/var/www/site1/
/var/www/site2/
/var/www/site3/
/var/www/site4/

You can also do it via

/home/user1/www
/home/user2/www
/home/user3/www
/home/user4/www

---

### Post by Norseman on 2010-01-08
Thank you for the great link and pointing me in the right direction.  I have much to learn.  The commands that are used to navigate around give me the feeling I am speaking in "tongues".  As with anything new, it takes a bit to get used to it.
Again, I appreciate your help.

---

