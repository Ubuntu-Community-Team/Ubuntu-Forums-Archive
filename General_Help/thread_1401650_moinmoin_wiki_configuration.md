---
title: "moinmoin wiki configuration"
date: 2010-02-08
forum: General Help
---

### Post by The Cog on 2010-02-08
I thought it would be a good idea to start a wiki for my dept. at work, and like the look of some of the features of moinmoin. 

I ran the wikiserver on my PC to try out, and it looks good except that it insists on being located at the root URL. We really want to put it on a sub-folder such as /wiki/ so that we can have our proxy just forward requests for /wiki/... to it.

I've spent 4-5 hours trying to find how to do this in the documentation, but it doesn't seem to be documented at all. There are however tantalising hints that moimoin used to be able to do this at some time in the past, perhaps with the "url_prefix" configuration that seems to be no longer documented or supported. 

I would really appreciate some help making this work, if it's possible.

---

### Post by gmargo on 2010-02-09
Thank you for the challenge.  I was able to install MoinMoin so that it appears to be in a sub-folder. It takes no space under the root directory and resides in a user-definable location.

Challenge: Install MoinMoin in a sub-folder
Expected difficulty: easy
System: Ubuntu 9.04 Jaunty Jackalope

Installed pre-packaged moinmoin and virgin apache2:
```

python-moinmoin      1.8.2-2ubuntu2.1    Python clone of WikiWiki - library
apache2              2.2.11-2ubuntu2.5   Apache HTTP Server metapackage
apache2-mpm-prefork  2.2.11-2ubuntu2.5   Apache HTTP Server - traditional non-threaded model
```Decisions:
Set up multiple Wikis; don't restrict to one.
Create directory to hold wiki data outside of /var/www.

Just for argument's sake, let's make two wikis, one for Engineering ("eng") and one for Human Resources ("hr").

A few commands to copy the necessary data:
```

export WIKIBASE=/home/wikidata
export WIKIDIR=$WIKIBASE/eng
export WIKIDIR2=$WIKIBASE/hr
mkdir -p $WIKIDIR/cgi-bin

cp -pR /usr/share/moin/data $WIKIDIR
cp -pR /usr/share/moin/underlay $WIKIDIR
cp -p /usr/share/moin/server/moin.cgi $WIKIDIR/cgi-bin

chown -R www-data:www-data $WIKIDIR
chmod -R ug+rwX $WIKIDIR
chmod -R o-rwx $WIKIDIR
chmod -R ug+rx $WIKIDIR/cgi-bin
chmod -R o-rwx $WIKIDIR/cgi-bin

# Copy virgin /eng/ to /hr/
cp -pr $WIKIDIR $WIKIDIR2

```Created two files: /etc/moin/wiki_eng.py and /etc/moin/wiki_hr.py.
They are copies of /etc/moin/mywiki.py and are customized for each.

Customized /etc/moin/farmconfig.py to support two wikis under /wiki/eng/ or /wiki/hr/

Added the following lines to the apache site configuration file
(/etc/apache2/sites-available/default or whatever)

```

# MoinMoin Configuration
Alias       /moin_static182/ /usr/share/moin/htdocs/
ScriptAlias /wiki/eng /home/wikidata/eng/cgi-bin/moin.cgi
ScriptAlias /wiki/hr  /home/wikidata/hr/cgi-bin/moin.cgi

```See attached 3 files: /etc/moin/farmconfig.py, /etc/moin/wiki_eng.py, /etc/moin/wiki_hr.py

Now after restarting the apache web server, the two wikis are visible under **[http://machinename/wiki/eng](http://machinename/wiki/eng)** and **[http://machinename/wiki/hr](http://machinename/wiki/hr)**

---

### Post by happyzax on 2010-02-09
I have just been playing with the latest version of MoinMoin and figured out how to put the wiki somewhere other than at the root of the web server.  First of all, I am assuming you have been using this page...

[**http://moinmo.in/HowTo/UbuntuQuick**](**http://moinmo.in/HowTo/UbuntuQuick**)  

There is a little comment in Quick Tips (Section 4) about changing the [FONT="Courier New"]WSGIScriptAlias[/FONT] setting in the MoinMoin WSGI configuration that is added to the Apache config ([FONT="Courier New"]/etc/apache2/apache2.conf[/FONT]).  So you would change yours to something like:

```
WSGIScriptAlias /wiki/   /usr/local/share/moin/moin.wsgi
```

What it fails to mention however is that you also have to set the *[FONT="Courier New"]url_prefix_static[/FONT]* setting in the [FONT="Courier New"]wikiconfig.py[/FONT] to a similar path, so that all the other content from MoinMoin is also found in the same place:


```
    # If you run your wiki script at the root of your site (/), just do NOT
    # use this setting and it will automatically work.
    # If you run your wiki script at /mywiki, you need to use this:
    url_prefix_static = '/wiki' + url_prefix_static
```

I hope this info helps you with your situation.  Good luck!

---

### Post by The Cog on 2010-02-09
Thank you for the pointers. I had been trying to do it under the server that comes with it, rather than having to learn all about setting up an apache server too. But last night I found a bug report that says the built-in server cannot run non-root, so it seems I have no choice but to get to grips with apache too. I will be following your advice here as soon as I get a new apache server installed.

---

### Post by The Cog on 2010-02-09
Well, I have success using happyzax's single wiki approach. Apache wasn't as fearsome as I thought it might be. I like the idea of having a wiki farm, so I might well try that later as well - I'm getting bold now.

Thanks for the help.

Edit:
I have now followed gmargo's approach but using wsgi not cgi, to set up another wiki on the same server for another department. I'm quickly growing to like moinmoin.

---

