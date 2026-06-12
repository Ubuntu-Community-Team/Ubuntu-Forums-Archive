---
title: "Time and date problem."
date: 2011-03-19
forum: General Help
---

### Post by jfbooth on 2011-03-19
Xubuntu 10.10

I am trying to keep time and date managed by NTP servers.  The utility for doing this opens a window where my time zone is selected (America/Chicago) and 'Keep synchronized with Internet servers" is selected.  Beneath that is Select Servers.  From that box, I select "ntp.tmc.edu (Texas, USA)" with a check mark and click CLOSE.

At some time I installed the ntp (Network Time Protocol) daemon in my system.

First sign of a problem is the window still says SELECT SERVERS.  Seems like it should show the server selected.

In any case, I found some info in another thread.  It said > Open a terminal window and type "sudo ntpdate" to automatically update your clock settings from the same source your atomic clock uses.

Here is the output from that:

**19 Mar 09:01:01 ntpdate[2739]: no servers can be used, exiting**

Then I tried the following .. as suggested in the other thread:

[B]jb@john-xubuntu:~/Desktop$ ntpdate pool.ntp.org
19 Mar 09:01:54 ntpdate[2743]: bind() fails: Permission denied[/B]

Then I tried:

[B]jb@john-xubuntu:~/Desktop$ ntpdate ntp.tmc.edu
19 Mar 09:19:34 ntpdate[2779]: bind() fails: Permission denied[/B]

Any help with this is appreciated.  Thank you in advance.

Edit:  Maybe everything is working fine ... the time/date returned from ntpdate command is correct.

---

### Post by tredegar on 2011-03-19
**ntpdate** needs to be run as root:
**sudo ntpdate ntp.tmc.edu**

---

### Post by MasterNetra on 2011-03-19
> **tredegar said:**
> **ntpdate** needs to be run as root:
**sudo ntpdate ntp.tmc.edu**

+1 put sudo before your commands

---

### Post by jfbooth on 2011-03-19
thank you Gentlemen.  Does this look right?

jb@john-xubuntu:~/Desktop$ sudo ntpdate ntp.tmc.edu
[sudo] password for jb: 
19 Mar 16:18:31 ntpdate[2976]: the NTP socket is in use, exiting
jb@john-xubuntu:~/Desktop$

---

### Post by tredegar on 2011-03-19
> 19 Mar 16:18:31 ntpdate[2976]: the NTP socket is in use, exiting
This means that ntp is already running (you must have done something to set this up)

**ps -Al | grep ntp** should show the process

---

### Post by jfbooth on 2011-03-19
> you must have done something to set this up

Yes .. I did with the Time/Date utility in Xubuntu.  The question is .. since the utility does not show the server I check marked as being 'selected', I wasn't sure it was working.  

It says to pick a server .. and I did.  I put a check mark by ntp.tmc.edu .. then it came back to the window saying Select Servers .. so I wasn't sure it was working.

The terminal command ```
sudo ntpdate ntp.tmc.edu
```

returned

```
19 Mar 16:18:31 ntpdate[2976]: the NTP socket is in use, exiting
```

So .. is the 'utility' as I have described it working???  The skunk in the woodpile is the freekin UTILIY does not indicate I selected a server  .. but I GUESS it is working if the service is running.  The whole issue is the behavior of the utility.  Starts with a window to pick a server ... new window opens, check mark a server and click OK .. comes back to window saying pick a server.

---

