---
title: "Does Database Crash Has Anything To Do With The OS Server Uses?"
date: 2009-07-01
forum: General Help
---

### Post by nakodari on 2009-07-01
My problem is that I use Ubuntu Hardy and have no plans to change it. It is working smoothly on my server for the past 6 months. For database I use Apache MySQL and recently it crashes almost after every 2 days or you can say randomly. When I try to access my wordpress blog, it gives error such as 'Database connection failed'.

This is what my apache error logs say before the database started going down:

[Tue Jun 30 19:22:47 2009] [error] [client 202.179.95.2] request failed: error reading the headers
[Tue Jun 30 20:13:20 2009] [error] [client 174.143.26.108] WordPress database error Table 'addictivetips.wpau_upgrade_log' doesn't exist for query DESCRIBE wpau_upgrade_log made by do_action_ref_array, call_user_func_array, wpdbBackup->cron_backup, wpdbBackup->db_backup, wpdbBackup->backup_table
[Tue Jun 30 21:09:18 2009] [error] [client 78.105.130.78] Invalid URI in request HTTP/1.1 200 OK
[Tue Jun 30 21:09:18 2009] [error] [client 78.105.130.78] Invalid URI in request HTTP/1.1 400 Bad Request

My question now is, why exactly does a database go down, just why? It seems like database can't scale itself. Secondly, does it have anything to do with the OS I use, in my case it is Hardy? I think the answer of later is NO.

For those who will recommend that I should increase the settings of my database, I have to say that my friend's blog has the same setup and can handle 25,000 uniques daily while mine is crashing with 7,000 uniques only. :( Any idea? 

PS... I have kind of lost hope, so if anybody can help me out that would be great!

---

### Post by FluffyElmo on 2009-07-01
It wouldn't be the OS. It looks like it's an error with that particular query, it expects to find a table wpau_upgrade_log in database addictivetips but it isn't there. If you've upgraded Wordpress lately your database schema may not be current?

In case it is Mysql when you get the error check to see if Mysql is still running and you can connect from the command line. You can also check the Mysql logs in /var/log/ to see if there are any clues. I've also seen database errors where the disk was almost full or where the disk was beginning to fail.

Based on the error you have though I'd assume it's a problem with your schema. Check to see if the table is actually there to start and go from there.

---

### Post by FluffyElmo on 2009-07-01
Also, regarding when the errors happen it seems to be a back-up script that's failing. There is probably a cron job that runs daily or on some other schedule. Check your cron jobs to see if any of the schedules match the timing you've been seeing. If so it's definitely a PHP/Mysql error and has nothing to do with the OS.

---

### Post by nakodari on 2009-07-04
@FluffyElmo Thanks for your awesome reply. So here is what I did, I was using a database manager plugin which optimized the database daily and at the same time another service made the backup. Maybe due to conflict and heavy load the database might have crashed. I have disabled the plugin to see if anything improves at all.

Secondly I don't think that there are any memory problems, normally my server takes 300Mb memory only and supports upto 2Gb of memory.

My var/log/mysql directory is empty, there are no logs there. To temporarily solve the problem I have disabled the backup plugin too that was constantly asking for  table wpau_upgrade_log in the database addictivetips. Now let's see if the database stops crashing, but if it still does, I will update you about the problem. :)

---

### Post by nakodari on 2009-07-05
My database has once again crashed. I have gone over and over again with the error log and found these two errors that occur before the database goes down.

[Sat Jul 04 08:32:45 2009] [error] [client 75.127.106.65] client sent HTTP/1.1 request without hostname (see RFC2616 section 14.23): /w00tw00t.at.ISC.SANS.DFind
[Sat Jul 04 19:32:20 2009] [error] [client 216.168.43.234] client sent HTTP/1.1 request without hostname (see RFC2616 section 14.23): /w00tw00t.at.ISC.SANS.DFind

The last two lines in my apache error logs are:

[Sun Jul 05 02:27:19 2009] [error] [client 78.40.248.119] Invalid URI in request  _csuid=4a4eb49d5ce1e79b
[Sun Jul 05 02:27:22 2009] [error] [client 78.40.248.119] Invalid URI in request -Alive: 300

Anything that I am doing wrong? If someone can understand what these errors mean and help me out I would be really thanksful.

---

### Post by nakodari on 2009-07-06
I just wanted to tell that the problem has been solved. Someone was trying to hack my server through brute method and I have blocked him using iptables. Now the database crash problem is solved. :)

---

