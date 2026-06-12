---
title: "Has my Ubuntu been hacked?"
date: 2011-10-15
forum: General Help
---

### Post by ligiopro on 2011-10-15
Last night, after I supposedly put my laptop to sleep, according to my logs, there still seemed to be a bunch of activity, namely the escalation of user privileges to root. When I got to my laptop this morning, it was in a cycle of resuming and sleeping ...


I've attached a section of my auth.log

---

### Post by Dangertux on 2011-10-15
> **ligiopro said:**
> Last night, after I supposedly put my laptop to sleep, according to my logs, there still seemed to be a bunch of activity, namely the escalation of user privileges to root. When I got to my laptop this morning, it was in a cycle of resuming and sleeping ...


I've attached a section of my auth.log


This log doesn't show in and of itself that your system was cracked. However it DOES show someone su root several times.

If this wasn't you, I would definitely be concerned. This log doesn't really help us determine if it's remote or local however this entry

```

Oct 15 02:10:32 lgp-laptop su[4327]: Successful su for lgp by root
Oct 15 02:10:32 lgp-laptop su[4327]: + ??? root:lgp

```

Is interesting because it appears the user fails to gain a shell. Another point of interest is that root is running a cron job, during this log. 

You should check to see what it is

```

sudo crontab -e

```

I would definitely be concerned. Are you running SSH or VNC or any other services? Or did you download software from an untrusted source?

---

### Post by ligiopro on 2011-10-15
It seems like whenever I put my laptop to sleep and whenever I resume it from sleep, there is a repeating sequence of:
```
Oct 15 02:10:32 lgp-laptop su[4327]: Successful su for lgp by root 
Oct 15 02:10:32 lgp-laptop su[4327]: + ??? root:lgp
```

This happens on my desktop as well. Both are running Lucid.

My laptop has had suspend/resume issues with kernel 2.6.32 and I had to upgrade to the 2.6.33 mainline kernel to get "proper" suspend/resume behavior, but it seems like there are still lingering issues with suspending and resuming. From my logs, it seemed like my laptop was intermittently coming out of sleep and going back to sleep. 

I don't recall doing anything that could obviously compromise my computer security. If there are remote attempts to escalate user privileges, shouldn't the auth.log show it as such. ie. some connection from some ip address?

---

### Post by Dangertux on 2011-10-15
> **ligiopro said:**
> It seems like whenever I put my laptop to sleep and whenever I resume it from sleep, there is a repeating sequence of:
```
Oct 15 02:10:32 lgp-laptop su[4327]: Successful su for lgp by root 
Oct 15 02:10:32 lgp-laptop su[4327]: + ??? root:lgp
```This happens on my desktop as well. Both are running Lucid.

My laptop has had suspend/resume issues with kernel 2.6.32 and I had to upgrade to the 2.6.33 mainline kernel to get "proper" suspend/resume behavior, but it seems like there are still lingering issues with suspending and resuming. From my logs, it seemed like my laptop was intermittently coming out of sleep and going back to sleep. 

I don't recall doing anything that could obviously compromise my computer security. If there are remote attempts to escalate user privileges, shouldn't the auth.log show it as such. ie. some connection from some ip address?

You are correct in your statement about remote connections from the most part. However, if a service was started which is malicious in nature, it may not necessarily be logged, although I'm not sure what the purpose would be of it logging any events if you were going to the trouble of hiding it to begin with.

I would err on the side of it being functionality of your machine, perhaps root executing a task on resume from suspend , like mounting drives, or something else. 

I would say you were not cracked.

---

### Post by pretty_whistle on 2011-10-15
I agree.  You were not hacked.

---

