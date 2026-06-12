---
title: "linked tables error"
date: 2010-05-31
forum: General Help
---

### Post by EmilHem on 2010-05-31
In phpMyAdmin im getting this message
"The additional features for working with linked tables have been  deactivated. To find out why click here."
and I'm wondering how I can enable the linked tables.
When I click the "here" link I get this at the bottom
```
$cfg['Servers'][$i]['tracking']  ... not OK [ Documentation ]     Tracking: Disabled
```

---

### Post by urobb on 2010-06-28
Hi, have you figured out what needed fixing yet?  I'm having the same problem.  The popular answer is that adding:

$cfg['Servers'][$i]['tracking'] = ‘pma_tracking’;

to /etc/phpmyadmin/config.inc.php

should fix the problem, but in my case this doesn't seem to make any difference.

---

### Post by sistematico on 2010-07-07
+1 :(
------------------------------ EDIT ------------------------------ 
Solved, close all tabs and re-open. :D

---

### Post by Mikorist on 2010-08-19
> **urobb said:**
> Hi, have you figured out what needed fixing yet?  I'm having the same problem.  The popular answer is that adding:

$cfg['Servers'][$i]['tracking'] = ‘pma_tracking’;

to /etc/phpmyadmin/config.inc.php

should fix the problem, but in my case this doesn't seem to make any difference.

isn't easy to resolve :lolflag:

this work after i add  table `pma_tracking` in phpmyadmin db ):P

Table structure for table `pma_tracking`
-- 

[PHP]CREATE TABLE IF NOT EXISTS `pma_tracking` (
  `db_name` varchar(64) collate utf8_bin NOT NULL,
  `table_name` varchar(64) collate utf8_bin NOT NULL,
  `version` int(10) unsigned NOT NULL,
  `date_created` datetime NOT NULL,
  `date_updated` datetime NOT NULL,
  `schema_snapshot` text collate utf8_bin NOT NULL,
  `schema_sql` text collate utf8_bin,
  `data_sql` longtext collate utf8_bin,
  `tracking` set('UPDATE','REPLACE','INSERT','DELETE','TRUNCATE','CREATE DATABASE','ALTER DATABASE','DROP DATABASE','CREATE TABLE','ALTER TABLE','RENAME TABLE','DROP TABLE','CREATE INDEX','DROP INDEX','CREATE VIEW','ALTER VIEW','DROP VIEW') collate utf8_bin default NULL,
  `tracking_active` int(1) unsigned NOT NULL default '1',
  PRIMARY KEY  (`db_name`,`table_name`,`version`)
) ENGINE=MyISAM DEFAULT CHARSET=utf8 COLLATE=utf8_bin ROW_FORMAT=COMPACT;[/PHP]

---

### Post by marcusEting on 2011-01-23
I was having some trouble with this, too. On serverFault I found an answer that mentioned this tutorial:

[Enabling Linked Tables in phpMyAdmn]("http://techblog.willshouse.com/2009/08/16/enabling-linked-tables-in-phpmyadmin/")

It's pretty detailed. Also the comments have a lot of good discussion and some troubleshooting advice. Hope it helps! ;)

---

