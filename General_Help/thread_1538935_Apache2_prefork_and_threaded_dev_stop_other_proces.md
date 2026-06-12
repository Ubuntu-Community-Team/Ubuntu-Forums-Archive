---
title: "Apache2 prefork and threaded dev stop other processes from auto starting"
date: 2010-07-25
forum: General Help
---

### Post by clmbngbkng on 2010-07-25
I've been trying to install ruby on rails for my server and in steps to get that going I need to install apache2-prefork-dev.
I am able to install ruby and get Apache to work together and deliver pages just fine until I reboot the system.

I've done some snooping around the processes running and it seems that once I've installed apache2-prefork-dev or apache2-threaded-dev Apache doesn't start automatically along with some other processes (about 20 total seem to not run - I am getting this number from the total "processes loaded" number that shows when you login).

I can get Apache to work just fine with /etc/init.d/apache2 start and the webserver is up and running but I'm not sure what else isn't loading and I would like to figure out how to fix this all.

At first I tried "sudo update-rc.d apache2 enable" thinking it was just Apache that wasn't running but those were already in place for auto starting and something seems to be hanging it up.

Some other info is I'm doing this on 10.04 server and its a fresh install with LAMP tasksel during setup and all other updates have been applied.

What have I missed? Any logs I need to look at or upload here? Thanks!



EDIT: I should also say that I have Bind installed and working and Apache works just fine before I install any of the devs.
Is this posted in the right place?

---

### Post by clmbngbkng on 2010-07-26
Shameless bump!

---

### Post by clmbngbkng on 2010-07-26
There must be something that can be done. Please help if you can!

---

### Post by clmbngbkng on 2010-07-26
After being on the ubuntu IRC channel someone pointed out that this might be tied into the runlevel problem that some people might be having. 

I checked this out by typing runlevel and I got "unknown" back as the output so I'm going to look into this problem. I'll be using some other posts on the forum.


Just wanted to post this here so I could mark this as solved since my problem is different than I originally thought it was at the start of this thread.

---

