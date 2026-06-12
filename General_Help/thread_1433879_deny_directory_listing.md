---
title: "deny directory listing"
date: 2010-03-19
forum: General Help
---

### Post by scoutdubna on 2010-03-19
I have set up Ubuntu 9.1 with Samba etc. as a web server.

The files are in /var/www and are shared through Samba as web.  The root directory and sub directories have index.htm files in them but unfortunately except for the root directory users can see the directory listing rather than the directory automatically producing index.htm  This is obviously causing security problems.

Can anyone tell me how to prevent directory browsing by users coming into the sever over the internet by a redirect URL from another site.

eg [http://xyz.co.uk/bigwebsite.com/](http://xyz.co.uk/bigwebsite.com/) where bigwebsite.com is a domain registered with a change ip server because I have a service which dynamically allocates an IP Address.

Hope you can help.

CHRIS

---

### Post by mridkash on 2010-03-19
You need to set Apache web server directives to turn off directory listing. Check for Options syntax, [http://httpd.apache.org/docs/2.0/mod/core.html#options](http://httpd.apache.org/docs/2.0/mod/core.html#options) 

```

      <Directory /var/www>
               Options -Indexes
             </Directory>     

```

---

### Post by scoutdubna on 2010-03-20
Thanks for that quick reply and it worked so far.   Some of the directories copied over have index.htm files in them and in these directories I can still list the files but if there is an index.html file then I cannot even when addressing the directory as 

xyzdomain.com/

This would appear to be a parsing problem.  Can you direct me to what to do to put this right so I don't have to go all the way through the directories and copy the index.htm files as index.html

Thanks

CHRIS

---

### Post by efflandt on 2010-03-20
My apache is very old, but looking through httpd.conf:

```
<IfModule mod_dir.c>
    DirectoryIndex index.html
</IfModule>
```This is a space separated list of default indexes, so you could change that to:

DirectoryIndex index.html index.htm

or whatever else you want to add (I have also used index.cgi for my own script to generate the index I want).

Also if you want NO automatic indexing when there is no DirectoryIndex file, do not use **Indexes** in **Options** for that path or parent path.

---

