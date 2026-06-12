---
title: "Program already running"
date: 2011-07-02
forum: General Help
---

### Post by ELMIT on 2011-07-02
I like to use Autokey, but since upgrade to 11.04 I do not get an icon into the top task bar.

When I try to start it, it says it is already running. If I kill it and restart, I still cannot get it.

I tried to figure out something by using tail /var/log/messages  but since 11.04 I don't have a /var/log/messages file anymore.

Any idea?

bye

Ronald

---

### Post by hawthornso23 on 2011-07-02
The top task bar in unity has a whitelist of applications allowed to put stuff in there. If you look in the [S] unity power user guide [/S]  [COLOR=Red]Natty known bugs, fixes and workarounds[/COLOR]  sticky thread[COLOR=Red] (look at post number 4)[/COLOR] there are instructions in there to add other applications (or even all applications) to this whitelist.

---

### Post by phlancelot on 2011-10-31
Further to the previous comment - I found it just as easy to follow the instructions left in post #5 of that sticky, in particular...

install dconf editor (should be in software centre)

open dconf editor

navigate to > desktop > unity > panel

to the only line entitled "systray-whitelist" add autokey such that the the value field should look something like this:

, 'Autokey']

log out of ubuntu and log back in

now when you run Autokey (I usually do this from the dash) you should see the blue A in the system tray, now you can configure all the text expansions you like!

Next step would be to add autokey to the list of startup applications so one doesn't have to manually launch the program each time you boot up... /em adds this to todo list

---

### Post by kapetr on 2011-10-31
Works not for me :-(  See:
[http://ubuntuforums.org/showpost.php?p=11411747&postcount=7](http://ubuntuforums.org/showpost.php?p=11411747&postcount=7)

---

### Post by altheablue on 2011-11-18
Thank you! Worked perfectly. :D

---

