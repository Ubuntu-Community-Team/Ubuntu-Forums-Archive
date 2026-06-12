---
title: "htaccess - default file in sites-available folder"
date: 2011-04-27
forum: General Help
---

### Post by Zidaps on 2011-04-27
I couldn't help but notice that there are some lines in the default file that resemble those that should be in a htaccess file. 

> AllowOverride None Options Indexes FollowSymLinks MultiViews
AllowOverride All
Order allow,deny
allow from all
etc...That said I have a few questions.

1. Is the default file performing htaccess roles? 
2. If I don't create a htaccess file i don't find one anywhere, does that mean the default file acts as the htaccess file until one is created?
3. If I create a htaccess file do I need to remove those lines from the default file? will they clash?
4. What if I don't want to create a htaccess file, how secure is my server without it?

And one final off topic question.
If I am running multiple virtual hosts, what happens to the default file? When I put my ip into a browser "http://ip.ip.ip.ip" I get a forbidden message. but all URLs point to where they are supposed to... Maybe its because I don't have an index file in the www folder.. (not at the machine, will try it later to see what happens)....

I know, lots of questions... Thanks in advance for all help provided.

---

### Post by Doug S on 2011-04-27
>  
1. Is the default file performing htaccess roles? 
 It can, and actually the apache docs recommend this method now. (Myself, I use the .htaccess method, because my site has a low traffic rate, and I find it easier).
>  
2. If I don't create a htaccess file i don't find one anywhere, does that mean the default file acts as the htaccess file until one is created?
 
 I believe the defaults are all to allow access, but yes the default file is the authority.
>  
3. If I create a htaccess file do I need to remove those lines from the default file? will they clash?
No, you do not need to remove the lines. You already have the one required line changed from the default of "AllowOverride none" to AllowOverride All", and that is all you need.
>  
4. What if I don't want to create a htaccess file, how secure is my server without it?
I don't really know, I guess it depends on content and such.
 
Please also see: [http://httpd.apache.org/docs/2.2/howto/htaccess.html](http://httpd.apache.org/docs/2.2/howto/htaccess.html) (or 2.0, or whatever apache version you are using.)
I don't have an answer to your last question.

---

