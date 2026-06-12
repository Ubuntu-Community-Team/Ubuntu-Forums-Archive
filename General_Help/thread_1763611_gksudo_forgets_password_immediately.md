---
title: "gksudo forgets password immediately"
date: 2011-05-20
forum: General Help
---

### Post by Neovos on 2011-05-20
This occurred sometime in the past couple of days, perhaps because of an update that I just blindly accepted or due to some tinkering of my own. But for some reason, my gksudo never remembers the password I put in there anymore. When I sudo in a terminal it remembers no problem, and my sudo-via-terminal also responds to the "timestamp_timeout=x" variable in /etc/sudoers as it should. But does gksudo have it's own "/etc/sudoers" file where you can override the caching period for the password or does it reference the regular /etc/sudoers also? I have no clue where else to look....

thanks in advance.

---

### Post by mc4man on 2011-05-20
What version of sudo do you have installed?
(the 1.7.4.X sudo treats the timestamp (actually tty_tickets)  differently than previously

---

### Post by Neovos on 2011-05-20
> **mc4man said:**
> What version of sudo do you have installed?
(the 1.7.4.X sudo treats the timestamp (actually tty_tickets)  differently than previously

```
$ sudo -V
Sudo version 1.7.4p4
```

I'm on Ubuntu Natty. What's different now about it?

Thing is I use gksudo so infrequent that this wouldn't be to much of a problem. But when adding and removing ip lists for moblocker for example, gksudo needed a password for EVERY list I tried to add. It was quite nuts because I have a huge password and I added about 20 lists.
 
Of course I did that once and now it's done, but I'd still like to understand the behavior.

---

### Post by mc4man on 2011-05-20
Well to put simply the 'timeout' only is on a current running instance. I'm surprised you said this
"When I sudo in a terminal it remembers no problem"
which is true and 'usually' also  not true.

If you were to open a terminal and go 
sudo apt-get update
Then whether or not you needed to enter a password, (you likely will have to ) _close that terminal_, re-open a terminal and try again the command again
You normally w/ 1.7.4 will be prompted again for the password

In previous versions of sudo the 'timeout' would happen for any use during the period set. (terminal, run, synaptic

There is a fix for 1.7.4, though while i suggested it no longer use here for various reasons (I use the 1.7.2 from maverick security updates in natty

---

### Post by Neovos on 2011-05-21
> **mc4man said:**
> Well to put simply the 'timeout' only is on a current running instance. I'm surprised you said this
"When I sudo in a terminal it remembers no problem"
which is true and 'usually' also  not true.

Right, I'm familiar with that behavior. Sorry if I was unclear however, forgetting across different terminal instances but remembering for the default 15 mins in the same terminal instance is exactly the behavior I have and want when using sudo.

My problem is that I cannot get that same behavior with gksudo. It forgets across any and all uses and instances immediately and It never did that before. Also I am unsure if gksudo references /etc/sudoers for it's timing or if it has it's own config somewhere.

---

### Post by mc4man on 2011-05-22
> My problem is that I cannot get that same behavior with gksudo. It forgets across any and all uses and instances immediately
Same difference, unless I'm misunderstanding you...

You open a root browser and enter password. As long as that browser is open you shouldn't need to re-enter for actions in that browser window, at least not for 15 min.
So are you saying that you can't act as root in the browser window?

If you re-open then that's a new instance, now requires a password
 
(with the new sudo same thing with synaptic - everytime you open you need a password, the 15 min time frame is irrelevant.

---

### Post by Neovos on 2011-05-22
I think I figured it out. What I was thinking was a bug in gksudo is probably a design flaw in mobloquer. Gksudo in a terminal works correctly:

```
$ gksudo nautilus /home
$ gksudo nautilus /home
``` 

It asks the first time and launches the second time without needing the password. 

However in mobloquer, when I enable a blocklist, it essentially runs the command "gksudo cp '/tmp/temp_blocklists.list' '/etc/blockcontrol/blocklists.list'" from the program and asks every time I enable a blocklist.

What caught my attention was that in previous versions, the program would ask for my password just once, and then continue to add lists without asking until I was done. Recently, gksudo pops up with that command EVERY time I enable a blocklist.

So I guess my next question is do programs act like terminals in that, like the "gksudo nautilus /home" example above, they act as a "session" and remember the password for the default time window? Does it depend on the program?

Of course I'm just remembering now that previous versions of mobloquer ran in root from the beginning....and this most recent version does not therefore answering my question about this particular issue....but I guess the question still stands about programs acting in their own "session" anyway.

---

### Post by mc4man on 2011-05-22
When you're running gksudo nautilus from the terminal and then re-running in that same terminal  it's the 'terminal's timeout' (tty_ticket

If you were to start gksudo nautilus from the run dialog (Alt+F2) then every time would require a password under the new sudo. Maybe the same for moblocker, never used...

( as mentioned I no longer will use the 1.7.4+ sudo for that and some other reasons and the option to allow 1.7.4 to work like 1.7.2, (!tty_tickets), while generally ok I also found to be unsuitable

---

