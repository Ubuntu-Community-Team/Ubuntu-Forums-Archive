---
title: "No sound on Dapper Drake?"
date: 2006-04-17
forum: General Help
---

### Post by Lynn Monsanto on 2006-04-17
Hi all,

I have Dapper Drake, flight 6 installed and all is well except for no sound.  My laptop has a Intel 82801G sound card.  I searched syslog and found no error messages.  I also searched the /etc/init.d and could see where audio is initialized/started.

Any suggestions?  Thanks!
Lynn

---

### Post by johnc4510 on 2006-04-17
Try simple first:
System>Preferences>Sound 
Make sure it is pointing to your sound card

---

### Post by Lynn Monsanto on 2006-04-17
[QUOTE=johnc4510]Try simple first:
System>Preferences>Sound 
Make sure it is pointing to your sound card[/QUOTE]

Default sound card: HDA Intel.  I already thought of simple first ;-)  Thanks!

---

### Post by Mr Fat Bat on 2006-04-18
Hi there!

I'm having the same problem with the installed version of dapper and have found a thread which may help : [http://www.ubuntuforums.org/showpost...70&postcount=6]("http://www.ubuntuforums.org/showpost...70&postcount=6")

I'll post as soon as I see if it works!

---

### Post by Mr Fat Bat on 2006-04-18
Hey there!

Having the same problem but I think I found a thread that may help:

[URL="http://www.ubuntuforums.org/showpost.php?p=781470&postcount=6"]
http://www.ubuntuforums.org/showpost.php?p=781470&postcount=6[/URL]

Oh and if you are new to Kernel compilitation then you should probably check this thread out as well:

[http://ubuntuforums.org/showthread.php?t=85064]("http://ubuntuforums.org/showthread.php?t=85064")

I'll post as soon as I found out if it works.

---

### Post by openmind on 2006-04-18
Another simple (but often overlooked) thing, check all your outputs are on (up) in 'Alsamixer'.

I think they are all set to 'Off' by default.

---

