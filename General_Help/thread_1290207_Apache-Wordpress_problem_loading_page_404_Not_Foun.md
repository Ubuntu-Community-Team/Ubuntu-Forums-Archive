---
title: "Apache-Wordpress problem loading page: 404 Not Found"
date: 2009-10-13
forum: General Help
---

### Post by anarchipur on 2009-10-13
**[SIZE=4]Hi,[/SIZE]**

I work with Ubuntu 8.10. I just installed the LAMP-server. Then I copied my already working local wordpress-blog dir from windows to ubuntu. I also dumped the database. Export and then import using the phpmyadmin were OK.

On Ubuntu my web directory  is /var/www/  

Apache works fine with php test scripts (e.g. [http://localhost/mytest.php](http://localhost/mytest.php)) 
workpress works fine as well; I can administer the blog and can see it ([http://localhost/mywpblog/](http://localhost/mywpblog/))
In my blog I have a couple of pages, "Main" which is the main page  and "Contact" which is another page in my blog. Both links are shown on the site.

a call of http//localhost/mywpblog/ opens the main page
Now I click the "Contact" page and I get the error:
[B]
Not Found[/B]

  The requested URL /mywpblog/contact/ was not found on this server.
   Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4.3 with Suhosin-Patch Server at localhost Port 80 

So just to test, I defined another page in wordpress admin called "test1". I see it on my site; when I click it I get the same error - cannot find /mywpblog/test1/

In wordpress admin I can see & administer this page, so it is there.

How can I solve this problem? Is this a problem with apache or with wordpres[B]s?

[/B]Many thanks for your help!!

anarchipur

---

### Post by hwttdz on 2009-10-13
Do you have the apache modules required by wordpress enabled, i.e. a2enmod rewrite and I think there's one other.

---

### Post by anarchipur on 2009-10-13
> **hwttdz said:**
> Do you have the apache modules required by wordpress enabled, i.e. a2enmod rewrite and I think there's one other.

Thank you, this helped! I did a2enmod rewrite and then changed the following in /etc/apache2/sites-enabled/000-default:
<Directory /var/www/>
        Options Indexes FollowSymLinks MultiViews
               # I changed the following line because of 404 Not Found error for wordpress pages
           #old:    AllowOverride None
               #new:
               AllowOverride all
        Order allow,deny
        allow from all
    </Directory>

So now I can see all pages.
:confused:
Of course as it is with software,  I discovered another problem; the content of my post and on some pages is not complete after the backup restore. I used  phpmyadmin import and export menues, and it had no errors. I also use the multipage toolkit plugin, and now I see it is not working, the sontent of my post reduced to the first page...

I don't think it is an apache problem..
Probably the backup was not complete and I did not notice..?

---

### Post by anarchipur on 2009-10-13
I looked at teh .sql dump file of my  database, and the content is there. However the text editor gedit in Ubuntu complained the file is in the format UTF-8 but some of the characters are corrupted. Well I used the german wordpress and wrote the blog in german using charackters like 'ü'. But under Windows I did not face any problems...
Well this should probably be another thread concerning wordpress..

Nevermind if you have an advice for me I will be happy.

---

### Post by az on 2009-10-13
> **anarchipur said:**
> 
Apache works fine with php test scripts (e.g. [http://localhost/mytest.php](http://localhost/mytest.php)) 
workpress works fine as well; I can administer the blog and can see it ([http://localhost/mywpblog/](http://localhost/mywpblog/))
In my blog I have a couple of pages, "Main" which is the main page  and "Contact" which is another page in my blog. Both links are shown on the site.

a call of http//localhost/mywpblog/ opens the main page
Now I click the "Contact" page and I get the error:
[B]
Not Found[/B]

  The requested URL /mywpblog/contact/ was not found on this server.
   Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4.3 with Suhosin-Patch Server at localhost Port 80 

So just to test, I defined another page in wordpress admin called "test1". I see it on my site; when I click it I get the same error - cannot find /mywpblog/test1/

In wordpress admin I can see & administer this page, so it is there.

How can I solve this problem? Is this a problem with apache or with wordpres[B]s?

[/B]Many thanks for your help!!

anarchipur

You can browse
http//localhost/mywpblog/
but you cannot browse 
/mywpblog/test1/

What about localhost/mywpblog/test1/ ?

---

