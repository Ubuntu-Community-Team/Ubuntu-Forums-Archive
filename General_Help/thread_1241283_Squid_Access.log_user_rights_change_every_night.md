---
title: "Squid Access.log user rights change every night"
date: 2009-08-15
forum: General Help
---

### Post by Jonathan Beaumont on 2009-08-15
As a relative new comer, I am a having trouble working out what it going on here.

Every night, the user ownership on Squid's access.log changes from proxy proxy to syslog adm.

I thought it was logrotate that was doing it, but doing a forcerotate of the logs doesn't, and I can't find what other daily process is causing this to happen. 

Of course when the log file rights change, I can't restart Squid without manually changing the rights. 

I was going to run a CRON job to change the ownership each day, but thought I would see if anyone could help with the source of the problem. 

I trust this is the right place to post this. I would be grateful for any suggestions.

---

### Post by cdlamore on 2009-09-24
I am sure you have already solved this problem but I thought I would post the solution for any other poor souls that get this problem going forward -
 
After some digging I did solve this exact issue listed in this posting on one of my servers.
 
The solution was to edit to the **/etc/syslog.conf **file and remove the references to squid at the bottom. I commented them out initially just to be safe, but once I made that change this pesky problem went away.
 
Hope this helps~:KS
Christie

---

