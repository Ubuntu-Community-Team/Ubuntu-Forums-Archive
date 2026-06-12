---
title: "The requested URL / was not found on this server."
date: 2006-02-22
forum: General Help
---

### Post by moutraji on 2006-02-22
Hello!!! I need an urgent help here!!!!!!! I setup a server on Ubuntu Breezy few days ago.. I've installed apache2, php4, mysql4, phpmyadmin, wordpress, hula, and all was working fine until yesterday!!!! I tried to install Ruby on Rails and was succeeded but when i tried to open the server [http://localhost](http://localhost), instead of being directed to the var/www folder with the stuff i've installed, i was directed to setup page of Ruby on Rails!!! After that i decided to remove Ruby on Rails to see if that was the problem... Unfurtiontly, after removing Ruby on Rails i wasn't able to get to the server and i was giving the following message!!!

Not Found
The requested URL / was not found on this server.

I tried to open localhost/testphp.php, it also give me the server was not found problem... I think i'v deleted some files that should'nt be delete it or changed some of files permission, i don;t know!!!! All I know now that i need someone to help me resolve this problem as soon as possable and thank you in advance!!!

---

### Post by suRoot on 2006-02-22
You just need to check the root path in your httpd.conf file & make sure it points to the correct location on the filesystem.  If you're unsure how to do that, post your httpd.conf here.

---

### Post by moutraji on 2006-02-22
Thanks for replying!!!! This is my httpd.conf file content and its located in etc/apache2

# This is here for backwards compatability reasons and to support
#  installing 3rd party modules directly via apxs2, rather than
#  through the /etc/apache2/mods-{available,enabled} mechanism.
#
#LoadModule mod_placeholder /usr/lib/apache2/modules/mod_placeholder.so

---

### Post by suRoot on 2006-02-22
Your httpd.conf file should be a LOT longer than that :D 

Sorry, I don't have apache installed on my Ubuntu box or I'd post one for you.  I'll leave this for someone who has apache running on Ubuntu.

---

### Post by moutraji on 2006-02-22
Thank you any way!!! I will be waiting here for someone to help me soon!!!

---

### Post by moutraji on 2006-02-22
Any help guys??????? Please!!!

---

### Post by suRoot on 2006-02-22
Here's a vanilla httpd.conf file.  You'll need to modify it to work on ubuntu - paths, etc...

[http://livenudefrogs.com/~anubis/apache/httpd-conf.shtml](http://livenudefrogs.com/~anubis/apache/httpd-conf.shtml)

Sorry, can't post it directly here as it's too large.

---

