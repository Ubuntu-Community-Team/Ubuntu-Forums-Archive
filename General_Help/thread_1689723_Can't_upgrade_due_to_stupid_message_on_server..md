---
title: "Can't upgrade due to stupid message on server."
date: 2011-02-17
forum: General Help
---

### Post by FeraTech on 2011-02-17
I am using Ubuntu 9.10 x64 Server

I am trying to do an "sudo apt-get upgrade"

However, every time I try to do the upgrade I get the following message

"mysql-dfsg-5.1 (5.1.38-1) unstable; urgency=low

  * Please read [http://dev.mysql.com/doc/refman/5.1/en/upgrading-from-5-0.html](http://dev.mysql.com/doc/refman/5.1/en/upgrading-from-5-0.html)
  * Make sure to do a REPAIR TABLE on all tables that use UTF-8 and have a
    FULLTEXT index.

 -- Christian Hammers <ch@debian.org>  Sat,  4 Jul 2009 02:31:21 +0200"

I press 

Ctrl+C to get out of the message and it completely cancels my upgrade.

I am stuck. How do I finish the stupid upgrade?

---

### Post by earthmeLon on 2011-02-17
[http://dev.mysql.com/doc/refman/5.1/en/upgrading-from-previous-series.html](http://dev.mysql.com/doc/refman/5.1/en/upgrading-from-previous-series.html)

Seems that upgrading to the new version of mysql requires manual backup/dump of your database.  Please read the above link in it's entirety before doing anything.

[quote=mysql]
For dump and reload instructions, see Section 2.13.4, &#8220;Rebuilding or Repairing Tables or Indexes&#8221;. Any procedure that involves REPAIR TABLE with the USE_FRM option must be done before upgrading. Use of this statement with a version of MySQL different from the one used to create the table (that is, using it after upgrading) may damage the table. See Section 12.4.2.6, &#8220;REPAIR TABLE Syntax&#8221;.
[/quote]

If you want to keep your current mysql and just upgrade other packages...
You can 'lock' your current mysql version by finding it in Synaptic Package Manager and marking it as lock/do not upgrade.  I have this issue with my graphics card, as upgrading will leave me with X failing to start.

---

