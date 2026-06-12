---
title: "Newb help with virtual host"
date: 2009-08-11
forum: General Help
---

### Post by shelzmike on 2009-08-11
Okay, I must be missing something easy here. I am running 9.04, have LAMP installed and installed PHPList. All good to go there. 

Now, I am having problems getting the virtual host to work for phplist.

Here are the facts:

[http://www.mysite.com/phplist/list/admin](http://www.mysite.com/phplist/list/admin)
 - this is what I want to be able to type in to get to all the files listed in the phplist directory. 

I can get to it currently this way: [http://www.mysite.com/www/web/lists/admin/](http://www.mysite.com/www/web/lists/admin/)

I have a virtual.conf file (in my conf.d directory) that has the following (though I am not sure why other than I got this step out of the documentation)

```
#
#  We're running multiple virtual hosts.
#
NameVirtualHost *
```

I also have a file (phplist) in my sites-available directory that contains the following information:
```

#
#   phplist (/etc/apache2/sites-available/phplist)
#

<VirtualHost 192.168.0.177:80>

    ServerName pftechgroup.dyndns.org
    ServerAdmin shelzmike@embarqmail.com
    DocumentRoot /var/www/www/web

    LogLevel warn
    ErrorLog /var/log/apache2/www_error.log
    CustomLog /var/log/apache2/www_access.log combined

</VirtualHost>
```

Now, I have tried using *:80 instead of an actual IP address, and still no go.

I also have a symbolic link from this file to the sites-enabled directory.

And the DocumentRoot is correct in the above file. 

So, what am I missing here? Whenever I try to navigate to [http://www.mysite.com/phplist/list/admin](http://www.mysite.com/phplist/list/admin)

I get a 404 not found. 

I have a bad habit of overlooking something very easy, so hopefully that is what is going on here.

Mike

---

### Post by P4man on 2009-08-12
This doesn't look right:

    DocumentRoot /var/www/www/web

Are you sure thats the right path?

---

### Post by shelzmike on 2009-08-12
Yeah, that is right as that is the document root that I made (based on a PHPList tutorial). I do not think that is what it HAd to be, but rather just what they put. I suppose I could have made it anything. 

I did get this corrected though. I had to use localhost:80 instead of *:80 (not sure why, but I did) in order to get it to work as I am testing it locally first. I will change it to public IP once I am done with the testing and set up.

Mike

---

