---
title: "Strange FirstClass email failure"
date: 2010-04-23
forum: General Help
---

### Post by dgove on 2010-04-23
I recently installed Ubuntu 9.10 on both my home and office computers (from the same disk).  One of the first things I installed was the FirstClass email program on both (this is the email client that my university uses). I believe I did the same thing at home and at the office, BUT, the one at home works fine and the one at school just gives me a "user id and password do not match message." I can get FirstClass to work with the school computer when I boot up with Windows.  Even under Ubuntu, I can get my firstclass email through the Firefox browser.  But there are a few features of firstclass that are not as easy through Firefox as they are using the FirstClass client directly.  
Naturally, our university IT guy - even the one who is the designated FirstClass expert had no idea what was going on.

I have tried uninstalling and reinstalling Firstclass, but the same problem persisted.  But what is the best way to uninstall?  Must I use the terminal?

One colleague suggested, I need to adjust my LDAP, but I don't know what this means either.

Any comments appreciated,
Thanks

---

### Post by cariboo on 2010-04-23
Can you copy the configuration file from the system that works to the other?

---

### Post by dgove on 2010-04-23
thanks - 

When I go to "configure" it's not so much a file as a few blanks that I left filled in with the defaults.  There are blanks for "Port Number"  "proxy port" "Proxy IP address" and "Buffer Size"  Each one has an associated pull-down menu.  The only that actually has more than one choice is port number.  I tried switching from "TCP Default (810)" to "TCP Default (510)".  I also tried toggling up and down a few random port numbers e.g.811, 812, 813.  but each of these changes just made my login in a new way.  Specifically, when I pressed the login button, the computer just beeped - no other reaction at all.  I did not even get my previous "userid and password do not match" window.

When I get home in a little bit I will check to see if there is any difference in the config menu there and post accordingly.

---

### Post by dgove on 2010-04-23
Update:
   Now, I'm home.  I did find a difference with the at-home computer.  The default at home was for Port Number to be    "TCP Default (510)" while at home it was "TCP Default (810)".  But recall, I already tried changing this at school and only got beeps.  At home, I switched it the other way, and also got beeps and then - after more than a couple of minutes waiting with the message "Locating server on network" came the message "Sorry there is no FirstClass server with that name on the network.  Check your connection setup.  [1044]".  When I switched back, it did work again, so at least I didn't break anything.

Still wondering if there is a config file separate from the config menu I found.

---

### Post by Kurtm on 2010-06-04
There is something fishy with the Firstclass client.
If you try to login by entering user id and password, you will most of the time get the error message "user id or password wrong". However, if you open the advanced part of the login screen, enter user id and password and then click on the save button, you will be logged in. Nothing seems to be saved, and you have to repeat the same thing next time you login. 

Also, sometimes the clients dies and makes a core dump.

---

