---
title: "Ubuntu 10.04 fatal problem to log-in"
date: 2012-06-22
forum: General Help
---

### Post by madeyemoofy on 2012-06-22
Hi there, I have a severe problem with Ubuntu 10.04. after log-in and I need help. Here some details:

1. switch on laptop and enter passphrase (harddisk encrypted) - OK
2. Log-in menu appears and since I disable the log-in password, Ubuntu starts up right away and the following error messages come:

Could not update ICEauthority file /home/wolfgang/.ICEauthority

followed by

There is a problem with the configuration server. (/usr/lib/lingconf2-4/gconf-sanity-check-2 exited with status 256

followed by

Natilus could not create the following required folders: /home/wolfgang/Desktop, /home/wolfgang/.nautilus
"Before running Nautilus, please create these folders, or set permissions such that Nautilus can create them"

and then there comes the Ubuntu background picture and nothing happens anymore.

This most likely happens because I switched off the log-in password and have the harddisk encrypted. Anyway, the problem started after the last update which required a restart.

Now, my questions are:
1. how do I get into a state that I can change the log-in password back on 
and 
2. what command would that be?

I hope somebody can help

thanx a lot in advance
Wolfi

---

### Post by madeyemoofy on 2012-06-23
Here is the solution
CTRL+ALT+F1 => login via terminal
CTRL+ALT?F7 => login via GNOME (now it does not matter that password is not aksed)

=> change settings back to ask for password at login with GNOMW

dada

hyvää Juhannus

---

### Post by aluminum on 2012-08-21
Hello, this is my first post on this website so I hope it helps. 
I had the same first two errors: "Could not update ICEauthority file /home/wolfgang/.ICEauthority" and "There is a problem with the configuration server. (/usr/lib/lingconf2-4/gconf-sanity-check-2 exited with status 256." There was also a third error regarding Dropbox and Nautilus etc. but because all these errors showed up at the same time, I think they should all be able to be solved in one shot. 
After searching the web, including this website, I managed to get rid of the first error, but the others remained and I still could not log in. 

Thanks to a lead on this website: [http://forumubuntusoftware.info/viewtopic.php?f=46&t=2550](http://forumubuntusoftware.info/viewtopic.php?f=46&t=2550)
I typed in the code:
```
sudo chown -Rc user /home/user
```
 (note the location of spaces, and substitute your username for "user")
This solved my problem and I was able to log in without error. 

If someone could try to explain *why* this worked, that would be much appreciated.

If after doing this the first error remains, I'll try to figure out what I did to fix that error alone.

Peace,
Aluminum

---

### Post by Bucky Ball on 2012-08-21
> **madeyemoofy said:**
> Here is the solution
CTRL+ALT+F1 => login via terminal
CTRL+ALT?F7 => login via GNOME (now it does not matter that password is not aksed)

=> change settings back to ask for password at login with GNOMW

dada

hyvää Juhannus

Nicely done. Please mark thread as 'Solved', if it is, to help others. ;)

Yes, possibly a needle in the haystack of encryption, auto-login and a Nautilus quirk ...

@Aluminum: That command would change the owner of your /home/user directory or partition. For the use of '-Rc' open a terminal and type:
```

chown --help
```

... and look for 'R' and 'c'.

---

