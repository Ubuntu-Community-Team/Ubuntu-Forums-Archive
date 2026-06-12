---
title: "Nanny Blacklist 11.04"
date: 2011-05-07
forum: General Help
---

### Post by Graves28 on 2011-05-07
For years my wife has been reluctant to move over to Linux because of the lack of Parental Controls. With Ubuntu 10.10 there was the Nanny app and the associated Blacklist app was available. Life was good!!! 

Upgraded all my computers to 11.04 and the associated Blacklist app is gone and now my house is in chaos!!!! Wife is threatening that I migrate everything back to Windows or move out. 

:confused:

Help!!!! How do I get the associated Blacklist app back?

---

### Post by magdelaine on 2011-05-11
I'm very new to Ubuntu myself which is why I can't tell you the exact command for installing "Nanny", but I do know that it came with the "Edubuntu" package that is available in the software center. Love edubuntu, by the way...great for kids!! In any case you should still be able to install Nanny independently of Edubuntu if you want to.

---

### Post by magdelaine on 2011-05-11
Ok, maybe this will help: [http://www.liberiangeek.net/2011/03/parental-control-ubuntu-11-04-natty-narwhal/](http://www.liberiangeek.net/2011/03/parental-control-ubuntu-11-04-natty-narwhal/)

---

### Post by dFlyer on 2011-05-11
> **Graves28 said:**
> For years my wife has been reluctant to move over to Linux because of the lack of Parental Controls. With Ubuntu 10.10 there was the Nanny app and the associated Blacklist app was available. Life was good!!! 

Upgraded all my computers to 11.04 and the associated Blacklist app is gone and now my house is in chaos!!!! Wife is threatening that I migrate everything back to Windows or move out. 

:confused:

Help!!!! How do I get the associated Blacklist app back?

Nanny is under software center. Just reinstall it.

---

### Post by Minime1 on 2011-05-11
I am also in a similar situation as Graves28. Gnome Nanny worked fine in Ubuntu 10.10.Now since upgrading to 11.04 i can't find the Blacklists admin gui to import and manage the Nanny.nbl database list needed for Gnome Nanny to work. It used to be found under: "System-Administration-Blacklists", but is no longer there in 11.04. I have uninstalled & installed Gnome Nany several times. I have also found something called Nanny-data in the repositories that i have installed, but can not find any gui for it nor am i able to run it from the terminal.

I don't want to manually allow/block sites individually and hence why the database [_**here**_]("http://projects.gnome.org/nanny/data/nbl/nanny.nbl") was very useful, but without the Blacklists gui i am not able to have it imported into Gnome Nanny admin Console and the projects site has very poor documentation link to their site is _[here]("http://projects.gnome.org/nanny")_.

Thanks for your time.

---

### Post by 84_K10Guy on 2011-05-11
> **Graves28 said:**
> Wife is threatening that I migrate everything back to Windows or move out. 


Wow, seems kinda harsh. Just check Software Centre as everyone else recommended.

---

### Post by Minime1 on 2011-05-11
> **magdelaine said:**
> Ok, maybe this will help: [http://www.liberiangeek.net/2011/03/parental-control-ubuntu-11-04-natty-narwhal/](http://www.liberiangeek.net/2011/03/parental-control-ubuntu-11-04-natty-narwhal/)

Hi Magdalaine,

i have seen this post a few days ago. Good tutorial to restrict pc time or just block a few websites, but unfortunately it is a very time consuming way if you wanted Nanny to block a whole category of sites say "porn" for example. The database i mention in my post above is maintained by guys from the university of Toulouse in France and they compile and group sites into categories that once you have it imported into Nanny via the Blacklists gui, you can then set Nanny to block "porn, drugs, violence" and so on and that is why i and others are looking for the "Blacklists" gui that is no longer found in Ubuntu 11.04.

---

### Post by soapee01 on 2011-05-24
This is less help, and more rant, but hopefully it'll give somebody else some ideas.

A couple of things here:


1. Under lubuntu, it flat won't work.  The deb is missing a dependency (nanny installs just fine).

sudo apt-get install gnome-desktop-environment (ugg) to get this working. I started going through these one by one, but I gave up, lacking time atm.  It wasn't anything obvious like all of the python depends in gnome-desktop-environment, glade, any of the reqs from the nanny readme, etc.

Errors I saw related to above: getting GdkPixbuf-CRITICAL errors in .xsession-errors, and lot's of ENOENT (No such file or directory) in strace.  nanny-admin-console would spit out "GtkSpinButton: setting an adjustment with non-zero page size is deprecated" or some such nonsense.


2. The readme on the nanny page says they've re-done the blacklist. [http://projects.gnome.org/nanny/data/nbl/README](http://projects.gnome.org/nanny/data/nbl/README)

3. nanny-data doesn't seem to do a dang thing. Not sure if /usr/share/nanny/pkg_filters/guadalinex/nanny.nbl belongs in /etc/nanny or not, but I doubt it.

4. The nanny developer site can be found here: [http://openshine.com/projects/](http://openshine.com/projects/)

Here's their new blacklist site: [http://nannycentral.org/](http://nannycentral.org/)
and the json list: [http://static.nannycentral.org/v/nannycentral/blacklists/blacklist.json](http://static.nannycentral.org/v/nannycentral/blacklists/blacklist.json)

If you notice, the above blacklist (5/24/11) doesn't have any categories. It does add to nanny (click a user-> click keys -> click web browser tab->configure THEN blacklists tab->Add->add the json blacklist above).  You'll see the nanny central 'repository'? listed but it doesn't do anything.

nannycentral.org -> Registration:
   This service is under testing. You must be invited to join us.[/QUOTE]

Thanks ubuntu, you really know how to make a guy love you...  broken package.

</rant>

I'll see if I can find something in the meantime that works. Maybe there's a way to format another list nanny wants, or somebody can find a man page somewhere... /usr/share/doc/nanny is basically empty.

Installing from maverick won't work either.  Tried modifying the deb file to get rid of <<python2.7 depedency, and installing python2.6. It could probably be made to work.

This looks interesting: [http://static.nannycentral.org/nannycentral-repository/pool/testing/n/nannycentral/](http://static.nannycentral.org/nannycentral-repository/pool/testing/n/nannycentral/)
$ nannycentral-manage --help 
Usage: nannycentral-manage subcommand [options] [args]

Options:
  -v VERBOSITY, --verbosity=VERBOSITY
                        Verbosity level; 0=minimal output, 1=normal output,
                        2=all output
  --settings=SETTINGS   The Python path to a settings module, e.g.
                        "myproject.settings.main". If this isn't provided, the
                        DJANGO_SETTINGS_MODULE environment variable will be
                        used.
  --pythonpath=PYTHONPATH
                        A directory to add to the Python path, e.g.
                        "/home/djangoprojects/myproject".
  --traceback           Print traceback on exception
  --version             show program's version number and exit
  -h, --help            show this help message and exit

Type 'nannycentral-manage help <subcommand>' for help on a specific subcommand.

Available subcommands:
  changepassword
  check_automatic_rehab
  check_black_list_elements
  check_medals
  check_pending
  check_pending_notifications
  check_pending_votes
  check_urls
  cleanup
  cleanupregistration
  compilemessages
  convert_to_south
  create_prependings_cache
  create_root_user
  create_test_elements_and_votes
  create_test_users
  createcachetable
  createsuperuser
  datamigration
  dbshell
  delete_expired_users
  diffsettings
  dumpdata
  flush
  generate_static_dajaxice
  graphmigrations
  inspectdb
  loaddata
  makemessages
  migrate
  nannycentral_initialization
  rebuild_avatars
  reset
  reset_flags
  runfcgi
  runserver
  schemamigration
  shell
  sql
  sqlall
  sqlclear
  sqlcustom
  sqlflush
  sqlindexes
  sqlinitialdata
  sqlreset
  sqlsequencereset
  startapp
  startmigration
  syncdb
  test
  testserver
  update_inactive_users_karma
  validate

Based on the above, it looks like they are building a community site for building a blacklist.  Just a guess though.  For now, it looks like we may have to just wait, or stick with Maverick.

Anyone else have any ideas?

---

### Post by Frogs Hair on 2011-05-24
This site has a link to the Nanny blacklist. [http://projects.gnome.org/nanny/](http://projects.gnome.org/nanny/)

---

### Post by soapee01 on 2011-05-24
> **Frogs Hair said:**
> This site has a link to the Nanny blacklist. [http://projects.gnome.org/nanny/](http://projects.gnome.org/nanny/)

Right. Any idea on how to add it? The old tool has been removed.

---

### Post by Frogs Hair on 2011-05-24
> **soapee01 said:**
> Right. Any idea on how to add it? The old tool has been removed.

I don't use it but it looks like you import the list .

---

### Post by soapee01 on 2011-05-24
I'd already tried that. It wants a .json file. If you download the file (via ppa or whatever) and try to add a link to it (eg /home/username/nanny.nbl) BlacklistManager.py is actually hard coded to prepend http:// to it.

In other words, thanks, but already tried that and it doesn't work.

---

### Post by linuxinstalledfromhdd on 2011-05-24
You purchase a router with hardware based parental blocker subscriptions. That's what we did. It's also possible that your router has this option already, but you would need to contact support direct. Your kids are smarter than you think probably. :)

---

### Post by soapee01 on 2011-05-24
> **linuxinstalledfromhdd said:**
> You purchase a router with hardware based parental blocker subscriptions. That's what we did. It's also possible that your router has this option already, but you would need to contact support direct. Your kids are smarter than you think probably. :)

Agreed. Untangle or SmoothWall fit the bill nicely in this case. I'm building this laptop (for free), for a guy's daughter. They have no money for extra hardware, and she floats to her mothers house where she's largely unsupervised (and only 7). Lubuntu/Edubuntu fit the bill nicely for her provided I can get the filtering to work.

Aside: I'd just set up squid (or tinyproxy on h/w this old), but having a gui for this fellow to manage himself would be much more beneficial. Might have to go that route for the filtering, and leave nanny there for the timekeeping.

FWIW, there's plenty of ways around routers if you're creative as well. Especially with laptops.

---

### Post by magneze on 2011-06-03
I've been looking into parental controls for Linux too. Nanny looks like exactly the right tool - easy to use and well integrated, but it just doesn't work. As others have said - the blacklist is empty.

I previously tried Dansguardian but it's ridiculously complex and by default seems to block every other innocent site as Japanese Pornography. I'm sure I could delve into it's configuration to find out why but I really would like something that "just works".

I've seen Privoxy recommended on TechRadar last year:
[http://www.techradar.com/news/software/applications/6-of-the-best-content-filters-for-linux-698307?artc_pg=2](http://www.techradar.com/news/software/applications/6-of-the-best-content-filters-for-linux-698307?artc_pg=2)

Anyone had any luck with anything other than Dansguardian or Nanny? (I want this running on the computer btw, not on the router)

---

### Post by magneze on 2011-06-03
So ... I emailed the developer about the empty JSON database and got this answer:

> Yes this is because you are using an unstable version of nanny than will integreate a webservice (nannycentral.org) still in beta status.

Problably in next weeks we will release an stable version of nanny.

:)

---

### Post by linuxinstalledfromhdd on 2011-06-03
> **soapee01 said:**
> Agreed. Untangle or SmoothWall fit the bill nicely in this case. I'm building this laptop (for free), for a guy's daughter. They have no money for extra hardware, and she floats to her mothers house where she's largely unsupervised (and only 7). Lubuntu/Edubuntu fit the bill nicely for her provided I can get the filtering to work.

Aside: I'd just set up squid (or tinyproxy on h/w this old), but having a gui for this fellow to manage himself would be much more beneficial. Might have to go that route for the filtering, and leave nanny there for the timekeeping.

FWIW, there's plenty of ways around routers if you're creative as well. Especially with laptops.

At 7 I don't give them a laptop or a cell phone.  It's just asking for trouble.  I'm a control freak.  I was thinking this was a teenager.  I  monitor what they do 24/7 with keyloggers.  If they break the rules using a proxy - they are grounded. bawhahahaha

-ogre

---

### Post by magneze on 2011-06-03
Monitoring keyloggers? You must have lots of spare time on your hands!

---

### Post by hawthornso23 on 2011-06-03
As I understand it you guys are using Natty right? Unity desktop? And there is some control application for this nanny thing that is supposed to appear on the  taskbar and isn't? 

The taskbar under unity now whitelists applications that are allowed to use it. If your program isn't on the whitelist it won't show up on the taskbar. Could that be the issue? If so there are instructions as to how to get rid of the whitelist around the place which might fix your problem.

---

### Post by magneze on 2011-06-05
No, that's not the issue. The application appears but doesn't work because of a missing data file.

---

### Post by Minime1 on 2011-06-08
> **magneze said:**
> So ... I emailed the developer about the empty JSON database and got this answer:



:)

Thanks for taking this a bit further. Guess we will have to wait until it is sorted by the dev.

---

### Post by Guido Tabbernuk on 2012-01-22
> **Minime1 said:**
> Thanks for taking this a bit further. Guess we will have to wait until it is sorted by the dev.
I suggest you should try to convert a blacklist to JSON format yourself, it shouldn't be too hard to do. If you do some basic research and see what exactly is needed for that, maybe somebody can help you, too.

---

