---
title: "Requesting .htaccess help"
date: 2011-03-27
forum: General Help
---

### Post by Newbii on 2011-03-27
Hello there,

My website is hosted on a Linux server via GoDaddy and I am trying to use an .htaccess file on my root directory to both password protect and redirect my site. When I put the code for the password protect in (site was already redirecting fine) the password protect function seems to work, but then when I am given access to the site, it gives me an internal server error message.

Here is the code that works alone:

rewriteengine on
rewritecond %{HTTP_HOST} ^www.xxxxxx.com$ [OR]
rewritecond %{HTTP_HOST} ^xxxxxx.com$
rewriterule ^$ "http\:\/\/xxxxxx\.com\/home1\.html" [R=301,L] #4ad019d4419c9

Here's the code I added to the above that does manage to execute a prompt to log in, but then when I am logged in, there is an internal server error:

AuthUserFile home/xxxxxx/html/.htpassword
AuthType Basic
AuthName "xxxxxx"
Require valid-user

What am I doing wrong?

Thanks in advance for any help. :KS

---

### Post by Newbii on 2011-03-27
I tried a few other options, and the above code actually "works" the best, if not for the server error.

I have gotten this far as a newbie non-programmer researching online, and I think I am close, but there is something I am missing that I'm not finding through other examples. I'd be much obliged if anyone has a minute to help?

---

### Post by SeijiSensei on 2011-03-28
Are you sure that GoDaddy allows you to configure basic authentication via .htaccess?  It's possible to disable that ability in the server's configuration; for example, apache2 for Ubuntu is configured that way by default.  I'm guessing that it's unlikely to be disabled in a large hosted setting, but it doesn't hurt to ask.  The fact you're prompted for the password suggests this isn't the problem.

You might also try adding an AuthGroupFile directive.  Even if you don't have a group file, you can include this directive and use /dev/null for the filename like this:

```
AuthUserFile home/xxxxxx/html/.htpassword
AuthGroupFile /dev/null
AuthType Basic
AuthName "xxxxxx"
Require valid-user
```

I'm assuming you built the .htpassword file correctly using Apache's htpasswd utility like this:

```

cd /home/xxxxxx/html
htpasswd -c .htpassword username

```

More importantly, if that html directory is where the site's pages are kept, it's the [*wrong* place]("http://httpd.apache.org/docs/current/mod/mod_authn_file.html#authuserfile") to put the password file.  For security, put it in your home directory, /home/xxxxxx/, outside of the html directory.

---

### Post by Newbii on 2011-03-29
**Arigato SeijiSensei!!** You solved my problem. Thankyouthankyouthankyou! 

It WAS a problem of the .htpasswd file, which I had named something else without coding it correctly. I simplified the whole thing by just calling the file .htpasswd.

Here is the code I'm now using that works on GoDaddy Apache servers to password protect my site, in case anyone else can use the info:

```
AuthUserFile /[COLOR=Red]yourabsolutehostingpath[/COLOR]/.htpasswd
AuthGroupFile /dev/null
AuthName "[COLOR=Red]Your text[/COLOR]"
AuthType Basic

require valid-user
```In the .htpasswd file is:

```
[COLOR=Red]username**[COLOR=Black]:[/COLOR]**[/COLOR][COLOR=Red]encrypted [/COLOR][COLOR=Red]password[/COLOR]
```Encryption generator: [http://shop.alterlinks.com/htpasswd/htpasswd.php](http://shop.alterlinks.com/htpasswd/htpasswd.php)

**Thanks again!** :)

---

