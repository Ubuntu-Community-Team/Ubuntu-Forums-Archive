---
title: "Configuring Apache and PHP to use same doc root."
date: 2010-02-02
forum: General Help
---

### Post by RFrenette on 2010-02-02
Hello,

I'm new to Ubuntu and installed Apache, Tomcat and PHP using separate packages. All work well but it seems that the default doc root for Apache and PHP are in different places as:

The following command to start Apache:
    sudo /usr/local/apache2/bin/apachectl start
brings me to the "Test Page for Apache Install" and shows the Apache logo--successful--when I hit [http://localhost](http://localhost)

The following to start Tomcat:
    sh /usr/local/tomcat/bin/startup.sh
brings me to the "Apache Tomcat" page--successful--when I hit [http://localhost:808](http://localhost:808)

And the following to start Apache for PHP:
    sudo /etc/init.d/apache2 start
brings me to a page that says, "It Works! This is the default web page for this server." when I hit [http://localhost](http://localhost)

Of Note: Regardless of which command I use to start Apache, if I then start Tomcat I can get to the "Apache Tomcat" page--successful--which is obviously good/fine as it's on a different port.

So, I'm wondering, is there a way to start Apache using the following:
    sudo /usr/local/apache2/bin/apachectl start
and be able to serve both .html and .php pages from the apache2 doc root: /usr/local/apache2/htdocs, I believe?

Also, could someone please tell me how to stop PHP from starting Apache on boot?

Thanks for any assistance.

Rob

---

### Post by RFrenette on 2010-02-02
Actually, in further trying to find an answer to my questions above, I found how to stop PHP from starting Apache at boot:

sudo chmod -x /etc/init.d/apache2

However, it seems to me, from the information I have found, that starting Apache from the following seems to be the norm:
    sudo /etc/init.d/apache2 start
versus starting it from:
    sudo /usr/local/apache2/bin/apachectl start

I am guessing that is because, after installing PHP, one would want to start the server using the Init script (/etc/init.d/apache2) from the PHP install so you could set the environment variables for PHP. Of course, I'm guessing here because, as I say, I'm new to all this.

Any thoughts on this would be appreciated.

---

### Post by RFrenette on 2010-02-03
Okay, how about this one:

Could someone please tell me how to find out where the page that says, "It Works! This is the default web page for this server." is when I hit [http://localhost]("http://localhost/")?

I thought it would be index.php, as it is the page that came up after I loaded PHP, but can't seem to find it on the file system.

Thanks for any help as I'm clearly stumbling here...

---

### Post by RFrenette on 2010-02-03
I know this stuff is pretty basic, but it did confuse me so I'll post it just in case there are any other Newbs that have the same questions.

What I have determined is this:

1) When you install the apache2 package (sudo apt-get install apache2), it uses the following:

    start command: sudo /usr/local/apache2/bin/apachectl start
    DocumentRoot: /usr/local/apache2/htdocs

2) When you later install PHP (sudo apt-get install php5), it uses the following:

    sudo /etc/init.d/apache2 start
    DocumentRoot: /var/www

It seems that the preferred method of starting apache is to use the init script (/etc/*init*.*d/apache2)*. As a result, you must place your documents (.html, .php, ...) in /var/www to serve them unless, of course, you manually change your DocumentRoot.

Note that, by default after PHP installation, the init script is run at boot-up so you don't manually have to start apache. However, if you need to stop the server, execute the following:

    sudo /etc/init.d/apache2 stop

and the following to bring it back up:

    sudo /etc/init.d/apache2 start

If you don't want apache to start at boot, execute the following:

    sudo chmod -x /etc/init.d/apache2

and +x if you change your mind later.

Well, that's what I've figured out. Don't know if will help anyone else but, as I say, I figured I'd throw it out there...

---

### Post by pirateghost on 2010-02-03
even without PHP, on a debian based apache install, the default doc root is /var/www

where do you see that it ever used /usr/local/apache2/htdocs?

as far as the preferred method to start apache goes.....thats the same preferred method to start any service/daemon in a debian based system (/etc/init.d/xxxx start/stop/restart/reload) unless you have something that did not install an init script, which is pretty rare for a debian system.

---

### Post by RFrenette on 2010-02-04
Thanks for the info on init scripts being the preferred method for starting any service/daemon.

And thanks also for correcting my assumption regarding the default apache doc root. I came to this conclusion as, when I started the server using the following:

sudo /usr/local/apache2/bin/apachectl start

, then hit [http://localhost](http://localhost), the page that came up was:

/usr/local/apache2/htdocs/index.html.en

Could you please explain why starting the server from /usr/local... would bring up that page and starting from init.d would bring up /var/www/index.html?

---

