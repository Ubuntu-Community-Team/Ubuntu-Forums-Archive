---
title: "Permission problems"
date: 2009-08-08
forum: General Help
---

### Post by settoloki on 2009-08-08
hi I am new to ubuntu and would search for this as I am sure it has been answered 1000 times but I have a problem.

I am using vsftp and webmin 
what I did is create a user in webmin with the home directory of /var/www/username 

gave it a password and all looked to be working great 
in my ftp client I connected to my ubuntu server with username and password I just created and it goes to the home directory I can upload and download files :D 

only problem is I seem to upload files with the wrong permissions not sure what permissions they have but whenb I upload web pages I cannot view them online till I chmod -r 775 /var/www/username 
I have tried doing a chown to the users directory but I am guessing webmin takes care of that when you add a new user to it. 
 I'm at a loss what to search for in these forums to solve my problem.

any help is greatly appriciated

---

