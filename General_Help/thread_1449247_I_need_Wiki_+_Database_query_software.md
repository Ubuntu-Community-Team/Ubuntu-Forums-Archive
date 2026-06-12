---
title: "I need Wiki + Database query software"
date: 2010-04-07
forum: General Help
---

### Post by jdackle on 2010-04-07
Hi guys!

I need some piece of software that follows the requirements bellow. I hope someone can advise me on what to use... :grin:

So here's the scenario:
1. I need some piece of software that will allow me to edit related articles in a wiki-like fashion. I will be the only one editing this "wiki" though. :grin:
2. I need to be able to do searches/queries on the wiki content in a very flexible but also very concise way:
   - The usual search for an expression in all articles or only some category(ies) but also:
   - Wiki links to other wiki pages based on configurable criteria, e.g. articles belonging to some category(ies): I mean something like right-clicking would open a sort of database form to perform a query that would use the said link as expression but would only be run after you'd chosen your other criteria.
   - If anyway possible, do the above for any selected text on the page you were watching... :grin:
3. Ideally this would be one single application of course. But I'm perfectly alright with coupling two or even more together as long as they do integrate with each other flawlessly. ;)

I'm not sure I'm making myself clear, so please tell me if you need some clarification.

I also have no idea whatsoever whether it is actually hard to find such software or it's actually under my nose (say in OpenOffice.org :lol: ). So just shoot away! ;)

Thanks in advance. :)

---

### Post by partloer on 2010-04-07
Hi jdackle,

One option that I think would work is MediaWiki. This is a web based solution that is just like Wikipedia.  I think this should satisfy your needs depending upon how it is setup.  Take a look and let me know what you think.  I can help you through the setup or answer more question.

[http://www.mediawiki.org/wiki/MediaWiki]("http://www.mediawiki.org/wiki/MediaWiki")

---

### Post by jdackle on 2010-04-08
Thanks, partioer. :)

Looks interesting. I'll check it out further and post anyquestions I might have then.

Thanks again. :)

---

### Post by jdackle on 2010-04-11
Ok, so I poked around a little and I think I could use MediaWiki with the Semantic MediaWiki extension and I guess it would fit my declared needs just fine. 8-)
( I could actually do the edits in OOo too! :lol: )

But I have a question:
How about the server?
I understand I must install the engine on a server but I'm really null at most of that...
Is there some kind of tool to easily setup a server for MediaWiki?
"Server specifications":
- Will be running on a single machine that will also be the only client 99% of the time; I might want to access my wiki using another PC every now and then but if that's too much hassle, I'll be (almost) just as happy to have it accessible from my personal PC only.
- Will preferably not be running all the time but only "on wiki access" - being the MediaWiki accessible through an webbrowser makes me clueless as to what kind of "wrapper-script", if any, I could use to turn it on and off... :-?

---

### Post by partloer on 2010-04-12
What you need to do for mediawiki is install a web server and some additional software (Apache, PHP, and MySQL).  I don't know of a install tool but installing Apache2 (web server) is not difficult and you can configure it many different ways to access it.  

```
sudo apt-get install apache2
```

For example you can set it up so that only you would access it on your computer or on a network you can allow access so that someone else can type on the IP address of your computer to access mediawiki.  If in the future you want to access this from the internet you can open it up to allow access.

To turn it off you could just shut down the web server.

---

### Post by Monotoko on 2010-04-12
A nice guide to follow for installing the rest (PHP etc)

[http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

---

### Post by jdackle on 2010-04-12
Thanks.

Yeah, I'd noticed the dependencies on Apache2, MySQL and PHP for the MediaWiki package. That was what kind of frightening actually! :lol:
I know Apache is no "basic" piece of software, same for MySQL and to a point PHP so... :P
But you did encourage me to try it, so thanks, partloer. 8-)
What I need to do is worth the effort. ;)

Thank you very much for the link, Monotoko. Will check it out. :)


EDIT:
So, I installed LAMP (Linux Apache MySQL and PHP) successfully using Monotoko's link and also this one: [http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-9.10-lamp](http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-9.10-lamp)
(really easy! ;) )

So... now I actually have to figure out access to my brand new webserver (only local machine for the moment).
I noticed on phpmyadmin there are four accesses to phpmyadmin (only or my whole server? :-s )? Three of them are the same user (root) and the other one is debian-sys-maint and all machines listed are aliases to the same single one: localhost naturally.
But what does that mean? Are those the only users with granted access to my machine (root and debian-sys-admin?). But... is that really related to granting access from my onw PC only?...
I guess this is getting a bit offtopic and there is certainly a lot of info on this elsewhere...

Once I get that sorted out, I'll post again.

Thanks again! :)

EDIT 2: I sorted out the local-access only to Apache "problem". FYI here's the link to the thread I made in linuxquestions: [http://www.linuxquestions.org/questions/linux-server-73/listen-127-0-0-1-80-on-apache-2-2-a-802074/#post3935834](http://www.linuxquestions.org/questions/linux-server-73/listen-127-0-0-1-80-on-apache-2-2-a-802074/#post3935834)
On to *really* installing and configuring MediaWiki now!

---

### Post by jdackle on 2010-04-16
So...
Apache2, MySQL and PHP (and PHPMyAdmin) are installed and apparently everything is well.

However... 
To install MediaWiki, I followed this:
[http://www.mediawiki.org/wiki/Manual:Installing_MediaWiki_on_Ubuntu_via_GUI_and_Synaptic](http://www.mediawiki.org/wiki/Manual:Installing_MediaWiki_on_Ubuntu_via_GUI_and_Synaptic)
At a give point, that guide says:> This section assumes you want your wiki's URL to be [http://localhost/mediawiki](http://localhost/mediawiki). If this is not what you want, change "localhost" to your preferred server name and "mediawiki" to your preferred URL alias in the following instructions.

First we have to set the server name for your new Apache server.

   1. Run in Terminal:

          gksudo gedit /etc/apache2/httpd.conf

   2. This file is empty by default. Add the following line:

          ServerName localhost

   3. Save and close file.

(more here)

Next you have to set the URL alias of the MediaWiki installation.

   1. Menu: Applications &#8594; Accessories &#8594; Terminal
   2. Run the following command to open Apache configuration file:

          gksudo gedit /etc/mediawiki/apache.conf

   3. Remove the '#' on the third line so that line reads:

          Alias /mediawiki /var/lib/mediawiki

(You can replace /mediawiki with any alias you want, such as /mywiki)So I followed those instructions to setup my wiki in [http://myserver/mywiki](http://myserver/mywiki) (the names are actually different than myserver and mywiki but they are only lowercase letters in both cases.

Further ahead in that guide:>    1. Open web browser and navigate to: [http://localhost/mediawiki](http://localhost/mediawiki) (if you changed the server name or URL alias in previous section, change the URL accordingly)So I did and the MediaWiki "Setup your Wiki" page was displayed as expected. And I did complete the setup process successfully.
*I had noted however that in the initial configuration test script, it was "detected" my wiki page was /mediawiki, not /mywiki.*
Also, when it came to (after completing the in-webbrowser setup process): >  Move LocalSettings.php

Run in Terminal:

sudo mv /var/lib/mediawiki/config/LocalSettings.php /etc/mediawiki/
I was unsure whether to move it to /etc/mediawiki or to /etc/mywiki. I tried both (only one at a time) and found that the page following the "Setup process completed" (or something like that) did not work with /etc/mywiki (first try) but did work with /etc/mediawiki (second try).
Then I looked at the address bar on my browser and saw [http://myhost/](http://myhost/)**mediawiki**/index.php/Página_principal . So I edited it to [http://myhost/](http://myhost/)**mywiki**/index.php/Página_principal and got a "404 Not Found". :(
Not even the simple [http://myhost/mywiki](http://myhost/mywiki) that was displaying the Apache "It Works!" page is working now! :(

As a final note, when I first got MediaWiki to use the /mywiki alias, I had to create a directory /var/lib/mywiki and I copied the contents of /var/lib/mediawiki into it.

Can anyone advise me on _exactly_ where I went wrong and/or how to fix it?

Thanks in advance. :)

---

### Post by jdackle on 2010-04-18
BUMP.

Anyone?


EDIT:
Erm, nevermind (for now)!
I had actually messed it up myself in a pretty silly way:
in /etc/mediawiki/apache.conf I put:```
Alias /mediawiki /var/lib/mywiki
``` being the correct: ```
Alias /mywiki /var/lib/mediawiki
```lol
It's fixed now so on to the initial configuring of my wiki! ;)

---

