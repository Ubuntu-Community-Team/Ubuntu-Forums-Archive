---
title: "Apache rewrite: can't turn it on"
date: 2010-02-10
forum: General Help
---

### Post by goldsby on 2010-02-10
I have done 
[INDENT]a2enmod rewrite[/INDENT]
and rewrite.load appears in the mods-enabled subdirectory.

My httpd.conf file contains
 [INDENT]  DocumentRoot "/usr/appl/prod/htdocs/"[/INDENT] 
[INDENT]    <Directory />
       [INDENT]Options FollowSymLinks
       AllowOverride All
       Order deny, allow
       Deny from all[/INDENT]
    </Directory>[/INDENT]
(I tried Allow from all instead of Deny from all, but that made no difference.)

I'm using rewrite rules that work with Apache under Windows, such as:
 [INDENT]  RewriteEngine on
   RewriteRule jobtest/type2       /monkey.php[/INDENT]
where monkey.php is in /usr/appl/prod/htdocs.

I've enabled the rewrite log but there's nothing in it, since Apache is doing no rewriting.

Any suggestions would be appreciated.

---

### Post by goldsby on 2010-02-10
Forgot to add that I am running Ubuntu 8.04 (32-bit).

---

### Post by eric_1982 on 2010-02-10
Look for this part at the top

        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>


change **AllowOverride None** to **AllowOverride All**

So your file default file should look something like this






        <Directory />

                Options FollowSymLinks

                AllowOverride None

        </Directory>

        <Directory /var/www/>

                Options Indexes FollowSymLinks MultiViews

                AllowOverride All

                Order allow,deny

                allow from all

                # This directive allows us to have apache2's default start page

                # in /apache2-default/, but still have / go to the right place

                #RedirectMatch ^/$ /apache2-default/

        </Directory>







Let me know if this helps

---

### Post by eric_1982 on 2010-02-10
Oh i forgot, I think the file you want to be editing is /etc/apache2/sites-available/default

my httpd.conf file is blank in the apache2 dir

---

### Post by goldsby on 2010-02-10
Eric--
Thanks for the suggestion, but I already (following suggestions I had found online) changed every AllowOverride I could find to All, even those that seemed to have nothing to do with the directories I am actually using.  Still no joy.

---

### Post by eric_1982 on 2010-02-10
So if you look in /etc/apache2/sites-enabled and your site name or default file, you see that change under your web directory path?

Can you just give me idea of what you are trying to redirect?
Are you using a CMS tool like drupal or anything like that? Do you have a .htacess file at all?

---

### Post by goldsby on 2010-02-10
Thanks for following this problem.

The sites-enabled/default is (was, see below) unchanged from the installation except where I have changed AllowOverride None to AllowOverride All.  It has Directory elements for directories /, /var/www/, /usr/lib/cgi-bin, and /usr/share/doc/, in all of which I have set AllowOverride All.  (It also sets a DocumentRoot of /var/www/.  But apparently the DocumentRoot in our httpd.conf overrides that (/usr/appl/prod/htdocs/), since if we do 
[http://localhost/script_name.php](http://localhost/script_name.php), which requires no rewriting, it finds the script.)  All our (php) scripts are in /usr/appl/prod/htdocs, so we don't actually use /var/www/, /usr/lib/cgi-bin or /usr/share/doc/ for any of our Web files.  

We have Directory elements in our httpd.conf file for / and for /usr/appl/prod/htdocs, in which we set AllowOverride All, the we also have the directive Alias /  /usr/appl/prod/htdocs.  The URL 
[http://localhost/script_name.php](http://localhost/script_name.php), which doesn't require rewriting, works.

It occurred to me the problem might be that we do not have a Directory element in sites-enabled/default file for /usr/appl/prod/htdocs, so I copied the one from httpd.conf over there, but it made no difference.

We're not using any .htaccess files.

---

### Post by eaguilar on 2010-02-10
Do you reload apache ?

And you should create a file under subdirectory sites-avalaible then you use the command line a2ensite for activate the page.

---

### Post by goldsby on 2010-02-10
Wow!
(Yes, I did remember to reload Apache).
I took all of the stuff (DocumentRoot, Alias, Directory, Rewrite) that refers to out site out of the httpd.conf file and put it into a sites-available file, disabled the default and enabled ours and it works!!!

Thanks!  Without that suggestion I might have wandered around in the weeds for any length of time.

---

