---
title: "Running daemons with their own users"
date: 2011-02-02
forum: General Help
---

### Post by effenberg0x0 on 2011-02-02
After some years of Ubuntu I am finally starting to grow a concern for learning better PC management and security policies. One of the things I noticed is that many of my "media-related" daemons (such as transmission-daemon, sabnzbd, sickbeard, couchpotato, etc) were running as myself (start-stop-daemon -c $me).
 
On a single user PC, I never been too interested on learning how to create and manage system users and system groups before, so I don't know much about it. 

So far I have created a user for each of these media daemons, with no home, no shell, no password and added them to only one group named "media-daemons".

My NAS (/media/nas) holds all the media files these daemons must manipulate. Therefore, this NAS is set like
$sudo chown root:media-daemons * -R && sudo chmod 770 * -R

Does that sounds right to you guys? When I try to sudo service daemonxxx start all I get are "permission denied" messages from the daemons not being able to access the directories they actually should...

Any tip appreciated.

---

