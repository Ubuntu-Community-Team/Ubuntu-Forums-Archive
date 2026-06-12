---
title: "Dropbox changes permissions. Script to watch for Dropbox changes?"
date: 2010-06-24
forum: General Help
---

### Post by drewsus on 2010-06-24
Hello all. I have a series of system usability bash scripts that I sync with dropbox (and share with other friends that I have set ubuntu up on) and then have those folders sym linked to ~/bin. 

The problem is, when I change something on one computer, the scripts lose executability on other computers. Obviously, this doesn't help anyone! 

First, I guess I will ask, is there a way to stop this from happening?

Failing that, is there a way that I can have Dropbox's events monitored so that when something is updated, it runs a script on my Script folder adding 'chmod +x' to all the bash scripts. 

This is the simple nautilus-script that I am currently using to easily batch change the modes:
```
#!/bin/bash
#token: nautilus-script
for FILE in *
do
chmod +x "$FILE"
done
```

Please, any help would be GREATLY appreciated!
Drewsus

---

### Post by thewump on 2010-07-07
Hey,

Just discovered specto (sudo apt-get install specto) and remembered seeing this thread when I was researching the same dropbox annoyance with permissions.

K

---

### Post by drewsus on 2010-07-07
Hmm looks promising. Ill install now, check its man pages and tinker around with it to see if it meets my needs!

---

### Post by drewsus on 2010-07-07
While the man page was useless (and rightfully so since its purely GUI) specto itself was far from useless and provided me with exactly what I was looking for. 

Thanks a lot **thewump**!

Now, it seems to me that Specto wants to have the app window open and if I close it, it closes the application all together. The only way around this that I could see was to have Specto always show a notification icon. I would like this to run purely in the background, any ideas?

---

### Post by thewump on 2010-07-07
That's a shame! Having said that, it's a pain in the *** that this then has to run on every machine that has Dropbox. I'm going to see if I can track down a way to talk to them about making this a feature.

In the meantime, I'm tempted to just put an hourly cron on a chmod _x script and be done with it.  I don't think that would hamper my usage.

K

---

### Post by drewsus on 2010-07-07
Whatever you end up doing to contact them, let me know and I will do the same. Power in numbers! (even if just two ha)

Ive thought about doing cron but Id rather it just do something only if a change happens. For me, an hour long wait could really mess up the dualhead XBMC home theatres I have set up for people and they are not technically inclined at all so it will just seem to be broken to them. 
I think its stupid that dropbox changes the permissions in the first place. 
At least Specto allows you to export and import your watches which at least makes it somewhat easy for me to make scripts to do most of work there and make it have a GUI element using zenity

---

### Post by thewump on 2010-07-07
I went through the HELP screen. It allows you to create a ticket.  In their defence, I guess they don't "change" the file permissions they just ignore the concept all together.

Sucks that Ubuntu one is such a disaster.

K

---

### Post by thewump on 2010-07-07
So I've just spent 3 hours messing with various things and supposed Dropbox Alternatives and this is getting frustrating.. because if Ubuntu One actually worked, this would all be taken care of.

I'm migrating from keeping a bunch of stuff in SVN and only some of it is executable. I also want to centralize things like the config files for gedit and similar.. so wondering if this permissions thing is just going to keep biting me in the ***.

I am fine with a one hour cron though.. so right now playing with keeping a central master on one of my servers, and using rsync across ssh to sync via cron.  I'll keep you posted.

K

---

