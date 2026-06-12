---
title: "Standards to manage linux hosts"
date: 2010-08-31
forum: General Help
---

### Post by Mba7eth on 2010-08-31
Hi all,
   I've been recently employed as a linux admin on around 100 linux desktop machines. 

I just wondering, is there any kind of standards to manage this huge amount of hosts. Any kind of document (e.g. a book, lessons learned, ... etc). 


Thanks

---

### Post by scorp123 on 2010-08-31
> **Mba7eth said:**
>  I've been recently employed as a linux admin on around 100 linux desktop machines. I just wondering, is there any kind of standards to manage this huge amount of hosts. Common sense. :D

BTW ... how did you get that job? Because IMHO if you're qualified you shouldn't be asking such questions .... just wondering :D

> **Mba7eth said:**
>  Any kind of document (e.g. a book, lessons learned, ... etc).  Hmmm ... I think it would be wise if you could tell us more about your background and level of experience? Are you a total beginner? If yes you probably won't last long on that job ... On the other hand if you already have some UNIX admin skills then those would be very helpful ...

---

### Post by Mba7eth on 2010-09-01
well, .... as you guessed just a beginner. 
I got only a little background..... I'm not alone on the job there are others with me also. 

If you good help me.

---

### Post by scorp123 on 2010-09-01
> **Mba7eth said:**
> well, .... as you guessed just a beginner. Ummmfff ... I fear you might be a little over your head. But OK ... you gotta start somewhere.

The first thing I'd do if I was you is to make sure you get a 2nd desktop. This is assuming you have a personal desktop, right? Get a second one. The first one is for serious working where you will write your documents, answer e-mails, browse the web, etc. The second one is for wreaking havoc, doing stupid things, blowing up, crashing and burning ... in short: experimenting. That second desktop should as far as possible be identical to the many 100 desktops you're supposed to take care of so you have more or less the same hardware. That way it's easier to reproduce problems should any problems occur.

If you can't get a 2nd desktop for experimental purposes you will have to make do with a virtual machine (e.g. Virtualbox?) ... However, _DO NOT_ experiment with your own personal work desktop. It makes you look bad and requiring other people to fix your own desktop undermines your position. And plus: being a member of the admin team you can't afford your desktop being down, not even a second. There might important mails coming in and what not and if you don't respond within a millisecond people are going to go crazy ... Yes, people have unrealistic expectations. And they don't like having to wait. So you can keep them cool by at least responding within a reasonable timeframe (within 30 minutes is good ...) which you can only keep up if you never ever mess with your work desktop! Bingo. So that's why you need a 2nd machine. Work on the first one, never ever mess with it. Mess with the 2nd one, never ever do anything serious with it.

> **Mba7eth said:**
> I got only a little background.....Does your employer know this?? Just being curious. If they employed you as "Junior System Administrator" then your lack of knowledge is perfectly OK and shouldn't cause trouble to anyone ... junior admins are not necessarily expected to know anything. That's why they are junior admins in the first place. If however you were employed as "Senior Administrator" ... then you might be in trouble. Or your employer might have unrealistic expectations about what you can do or can't do? Just make sure you and your employer are on the same page ...

As for background: You have to read. A lot. And you better start immediately.

To my apprentices (who too have zero knowledge when they are condemned ... ahem ... given the priviledge to work with me :twisted: ) I always suggest to start with this book:

**"Linux for Dummies"**
[http://www.amazon.com/Linux-Dummies-9th-Richard-Blum](http://www.amazon.com/Linux-Dummies-9th-Richard-Blum)

+ it covers the basics
+ it's written in a funny style so you'll be motivated to get through it fast
+ it's also good for reference and looking up stuff 

When I was a newbie admin back in 1998 I always kept a copy of "UNIX for Dummies" in my desk ... just in case :D


Once you have the basics the next thing you have to learn is: backups. Seriously. Backup, backup, backup, backup, backup. **Your life will depend on it.** [COLOR="Red"]It's one of the most asked things: ***"Do you have a backup of that??"*[/COLOR]** ... And for an admin there is nothing worse than having to admit **[COLOR="RoyalBlue"]*"uuhhhhm, nope, we didn't have a backup of that. Uhhhmmmm ... was that stuff important somehow ... ??"*[/COLOR]**  <== **DONT EVER** get into that situation. **[COLOR="Red"]You will make backups. No f****ing excuses. Period.[/COLOR]** Because nobody will give a sh** if you can make up excuses or not. All people want is their backup and it's your job to make sure they get their data back when and if they want them back.

Sorry for the harsh language but I can't stress this enough. Give people their data back and you'll be their hero, again and again. This is what gives you respect, prestige and a good reputation. Lose their data and you will have to find a new job fast.

So this is the book you will live by:

**"Unix Backup & Recovery"**
[http://www.amazon.com/UNIX-Backup-Recovery-Curtis-Preston](http://www.amazon.com/UNIX-Backup-Recovery-Curtis-Preston)


Yes, the book is old (printed in 1999) but it's still valid. There are other books out there that cover specific backup tools but this is where you start.

Once you appreciate and realise how important backups are I recommend you head here:

[http://www.bacula.org/en/](http://www.bacula.org/en/)

Bacula is rock-solid. I know a few Swiss and Austrian banks where they use it. You want backups of your many 100 desktops? You want Bacula.


Last but not least ... key to surviving on this job is being informed. There is nothing worse than a clueless admin who still keeps doing things like they were done 20+ years ago. Computer OS need their regular updates ... but so do you!! So I recommend you read IT-related news sites. Not every site ... pick a few good ones and then stay with them. My favourites:

[http://www.h-online.com/](http://www.h-online.com/)  (I actually read the German original: [www.heise.de](www.heise.de))
[http://www.linuxtoday.com/](http://www.linuxtoday.com/)
[http://www.theregister.co.uk/](http://www.theregister.co.uk/)



> **Mba7eth said:**
> I'm not alone on the job there are others with me also.  That's good. And bad. Make sure you get along with each others and do things together as a team. Having a bunch of admins working against each others (e.g. by withholding important information, doing things differently, settings different passwords, etc.) is just painful and working in such a team is not worth it.

Given that you are not alone I'd recommend you split up responsibilities? Dude number one takes care of desktops #1 - #50, dudette number two takes care of #50 - ... and so on, the dude with a hang for web design takes care of the web pages and the internal Wiki where you will share your knowledge, the lady with the excellent writing skills will take care of the trouble ticketing system, the guy with the best network skills takes care of the firewalls, the routing and the LDAP server, and so on.

Non-IT people always expect their IT folks to be super specialists in *every* topic ... but this just isn't realistic. Just as we can't all be nuclear scientists we can't all be gurus at network design, IT security or shell programming ... Some people are better at certain things. You will need to find your niche and find it fast and then keep updating and upgrading your knowledge.

Above all the most important rule is: *Be a team player and be useful to the team.* **And always respect your local BOFH.** :twisted:

---

### Post by Mba7eth on 2010-09-07
scorp123, 
Thanks a lot for the information. Linux for dummies is already on the way. 

I really appreciate your help; and i wish i can one day return this favor to you :) 

You owe me one

---

