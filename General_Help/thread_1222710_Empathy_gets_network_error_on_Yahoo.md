---
title: "Empathy gets network error on Yahoo"
date: 2009-07-25
forum: General Help
---

### Post by fballem on 2009-07-25
Currently running Ubuntu 9.04 AMD64 Desktop. I've installed Empathy from the repositories.

I get a network error when I try to connect to my Yahoo connect. I know that the username and password are correct, because I can connect through the web.

I'm wondering if the problem could be a port (the default is 5050), but I don't have enough knowledge to diagnose or fix the problem if this is the case.

Any help to get Yahoo working through Empathy would be much appreciated.

Thanks,

---

### Post by B Crowther on 2009-07-27
Similar story to fballem, but on a different protocol: 64 bit 9.04 Desktop, just changed to Empathy instead of Pidgin, all has been working fine until just now, when I have started to get the network error message on MSN - my Yahoo is still fine.

Also get an error telling me I cannot make file transfers because the intended recipient doesn't have facilities to receive them. This is a bit of a backward step from Pidgin, which would transfer files via MSN and Yahoo, but not GTalk.

Voice and video only work on GTalk, but that is one more protocol than they worked on in Pidgin.

Whether it is Pidgin or Empathy, there ain't a lot of difference in performance. Skype is still the Rolls Royce app for Linux, if only I could get my Windahs Hillbilly mates to use it I could live happily ever after.

---

### Post by B Crowther on 2009-07-27
Hmmm, just saw a suggestion to try "killall telepathy-butterfly" in another post: did that and restarted Empathy, MSN is back.

---

### Post by hoazin on 2009-07-27
Had the same "Network Error" problem with MSN. Tried the "killall telepathy-butterfly" thing and it came back to life ...

---

### Post by sarfarazkazi on 2009-07-27
Go to Edit > Accounts and in the Server box add cn. at the beginning. For example, if the Server box says "scs.msg.yahoo.com" then change it to "cn.scs.msg.yahoo.com"

Hopefully, this will fix your connection problem. And don't forget to disable and then re-enable the account for changes to take effect.

---

### Post by Vevmesteren on 2009-09-17
is the "cn." a yahoo only solution? In any case, do you care to elaborate as to what this "cn." means, what server are we submitting our user data to when connecting to this server?

thanks

---

### Post by zeroseven0183 on 2009-09-18
Still has Network Error after adding **cn.**

---

### Post by ben2talk on 2009-09-20
> **B Crowther said:**
> Hmmm, just saw a suggestion to try "killall telepathy-butterfly" in another post: did that and restarted Empathy, MSN is back.

Indeed, killing butterfly restored my connection one time. I was trying to stay in contact, and Pidgin logged in very quickly (not that it hasn't shown some difficulty with MSN before).

This isn't a fix, though, and doesn't work every time. Is this an issue with MSN trying to outlaw clients?

I did notice, during current bloat upgrades - Live Messenger is disabled to force the upgrade now. The upgrade for Messenger is 140MB - and further inspection reveals a lot of parallel installations (Microsoft offer you the chance to select ones you wish to install - but they're pre selected for you in typical 'let's push it' fashion).

Reading the EULA reveals that by having a Live account, you agree not to use said account with any UNAUTHORISED messenger. It appears that Microsoft may be making life difficult for Empathy.

Any thoughts on this?

---

### Post by xghstst0riesx on 2009-09-29
I've tried the above suggestions and still get a network error. Anyone know what the issue is? Is Empathy also affected by the Yahoo protocol change that broke Pidgin Yahoo support?

---

### Post by n2dabloo on 2009-12-24
Bump, I'm getting the "network error" as well with Empathy trying to access my yahoo messenger account.  Oh well, it looks like I'll be sticking with Pidgin and Kopete

---

### Post by earthbound01 on 2010-05-24
I'm still even now getting these darned network errors.

---

### Post by yippy on 2010-05-26
Apparently "Network Error" is the only error message it knows.  I was getting that today and it was because my login name was wrong.  Double-check your login info just in case.

---

### Post by roeldebacker on 2010-07-29
great help. 
I used my e-mail adress to connect to facebook chat but apparently you need to use a username. 
It's announced but as a well-educated computer user: I NEVER read manuals :p 

better start doing that :rolleyes:

---

### Post by seanbw on 2010-08-31
I read this  message and it resolved my problem.
[http://ubuntuforums.org/showthread.php?t=1522691&highlight=empathy,+yahoo](http://ubuntuforums.org/showthread.php?t=1522691&highlight=empathy,+yahoo)
or to summarise: when entering your user name, dont add the @yahoo.com or equivalent part.

---

### Post by chunky bacon! on 2011-01-26
> **earthbound01 said:**
> I'm still even now getting these darned network errors.

Bump.  Me, too, and so far, none of the resolutions I've seen have helped.

User/pw is fine (double checked through web client).

:confused:


Edit:  This appears to be a problem in Pidgin as well, so perhaps this is something to do with Yahoo.  I noticed from a google search on this issue with Pidgin that in 2009, people were having issues with this and were plugging different servers into the account settings on Pidgin.  I think Yahoo has shut that down as well.

Also, Yahoo Questions removes any questions dealing with this as somehow violating a policy, so perhaps I'll just stick with the google chat accounts, and say good bye to yahoo messenger.

---

### Post by alinajafi on 2013-03-11
Hello everyone.

I have a workaround for this problem. Check if this solves your problem:
When you get "network error" open **System Monitor** and end "**telepathy-haze**" process. Then in **System Settings > Online Accounts** switch your Yahoo account **OFF** and **ON**.

---

