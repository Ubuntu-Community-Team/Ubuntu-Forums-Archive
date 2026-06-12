---
title: "Can't get .htaccess to work on 10.10"
date: 2010-12-05
forum: General Help
---

### Post by h1ll37 on 2010-12-05
Like I said .htaccess won't work on 10.10

All the guides seem out of date and I can't seem to find much recent stuff on it.

When i try and change AllowOveride to All instead of None and I put something in the .htaccess folder (not something random a real... err whatever it's called) it gives me this:

"Internal Server Error

The server encountered an internal error or misconfiguration and was unable to complete your request.

Please contact the server administrator, webmaster@localhost and inform them of the time the error occurred, and anything you might have done that may have caused the error.

More information about this error may be available in the server error log.

Apache/2.2.16 (Ubuntu) Server at localhost Port 80"

Thanks,
h1ll37

---

### Post by Doulos1 on 2010-12-05
What exactly are you putting into .htaccess? Did you try using a blank .htaccess file to be sure it is your content that is causing the error?

What version of php are you using?

---

### Post by SeijiSensei on 2010-12-05
> **h1ll37 said:**
> When i try and change AllowOveride to All instead of None

AllowOverride has two r's in it.  Does yours?

> More information about this error may be available in the server error log.

Did you check the logs? They're in /var/log/apache2.  You'll need to use sudo to read them.

---

### Post by h1ll37 on 2010-12-05
SeijiSensei:
Yes mine does type-o ;p

Here is my error log: [http://paste.ubuntu.com/540101/](http://paste.ubuntu.com/540101/)

Doulos1:
I am using PHP5, and yes I tried making the htaccess folder blank, it works then.

---

### Post by lisati on 2010-12-05
I'm not quite sure why, but your server seems to be tripping up on something in your .htaccess file that refers to 'RewriteEngine':
> /var/www/.htaccess: Invalid command 'RewriteEngine'

---

### Post by h1ll37 on 2010-12-05
Lisati:
Yeah that's what a guy in the ubuntu IRC for "httpd" said but he's not much help, he's kinda being a d... yyeah lol.

---

### Post by Doulos1 on 2010-12-05
htaccess is working, otherwise you wouldn't be getting the error message.  As I am sure you know, that means your server doesn't like something inside htaccess.  Post the contents of your htaccess file.  I have had issues with php5.3 and htaccess before, though not the same issue you are having.

---

### Post by h1ll37 on 2010-12-05
It ended up being i didn't have mod_rewrite enabled.

I decided to just use the vhost file which I didn't know I could do before ;p

On an off-note if you guys ever want to meet some real internet douche bags go ahead and go on freenode.net irc channel is #httpd

They helped but in the douchiest ways they could think of. Thanks for trying to kindly help me to all you guys.

---

### Post by lisati on 2010-12-05
> **h1ll37 said:**
> Lisati:
Yeah that's what a guy in the ubuntu IRC for "httpd" said but he's not much help, he's kinda being a d... yyeah lol.

Apologies for my reply not being more helpful: the best excuse I can come up with at the moment was that I was using a Windows (XP) machine at work, and didn't have chance to research more. :D

---

