---
title: "Creating a LAMP Menu like WAMP Server?"
date: 2010-06-09
forum: General Help
---

### Post by Varenne on 2010-06-09
Curious if anyone has already created something like this. I did a rather exhaustive search of the forums here and via Google with no luck.

I'm moving all of my development sandboxes over to Ubuntu from Windows so I figured I'd ask before building one from scratch. 

What does it do?
Basically it gives you a menu to access the localhost page with version info, alias, installed extensions, project folder links, plus sub menus for Apache, PHP and MySQL, links to files that often need editing, ability to add and/or activate more extensions, modules, start/stop and install/remove services.

I think this would be extremely useful, especially for those just starting out with LAMP on Ubuntu, but also for experienced users as well. And with more and more getting involved with web applications it certainly wouldn't hurt. Maybe even add it to the ubuntu-lamp-server install as a basic feature.

You can see screen captures here: [http://www.wampserver.com/en/presentation.php](http://www.wampserver.com/en/presentation.php)

Cheers all,

Varenne

---

### Post by saa on 2010-06-17
@see [http://www.launchpad.net/lampmenu](http://www.launchpad.net/lampmenu)

---

### Post by Varenne on 2010-06-18
Thanks saa, this is exactly what I was looking for!:popcorn:

When I have a chance I'm going to recommend (not sure where yet) this be the default install (a new package?) when users setup a desktop install of Ubuntu with server/LAMP features.

As I mentioned before so many are moving into web-based application development; Drupal, Joomla, WordPress, etc. and this will go a long way in smoothing out that process.

I took a look at the server related documentation concerning the default setup for LAMP and see a need for some minor improvements as it relates to having this as a desktop LAMP-for-development-only stack. For one, the Home folder should IMO be where the www folder (at the very least) is created not in a root controlled folder. And personally it should all be created there, it just makes it easier to learn and manage.

Thanks again,

Varenne

---

### Post by Varenne on 2010-06-19
Bummer that it only works for Ubuntu 10.04. I'm using 9.04 and didn't care too much for the performance I experienced with 9.10 or 10.04.

Continues searching...

---

