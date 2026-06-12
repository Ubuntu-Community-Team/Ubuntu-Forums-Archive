---
title: "How do I add users to ProFTPD-mod-mysql?"
date: 2011-07-16
forum: General Help
---

### Post by jamespuckett on 2011-07-16
Hey, I need to know how to add users and groups with proftpd. I have a mysql database setup and configured with it but Im not sure how to add users or groups as I do not know how to script in mysql.

My database is setup as such, 
SET NAMES utf8; SET foreign_key_checks = 0; SET time_zone = 'SYSTEM'; SET sql_mode = 'NO_AUTO_VALUE_ON_ZERO';  DROP TABLE IF EXISTS `groups`; CREATE TABLE `groups` (   `groupname` varchar(30) NOT NULL default '',   `gid` int(11) NOT NULL default '0',   `members` varchar(255) default NULL ) ENGINE=MyISAM DEFAULT CHARSET=latin1;   DROP TABLE IF EXISTS `users`; CREATE TABLE `users` (   `userid` varchar(30) NOT NULL default '',   `passwd` varchar(128) NOT NULL default '',   `uid` int(11) default NULL,   `gid` int(11) default NULL,   `homedir` varchar(255) default NULL,   `shell` varchar(255) default NULL,   UNIQUE KEY `userid` (`userid`),   UNIQUE KEY `uid` (`uid`) ) ENGINE=MyISAM DEFAULT CHARSET=latin1;

---

