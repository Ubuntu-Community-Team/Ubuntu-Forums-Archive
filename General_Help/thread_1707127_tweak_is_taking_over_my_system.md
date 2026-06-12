---
title: "tweak is taking over my system"
date: 2011-03-14
forum: General Help
---

### Post by gcomito11 on 2011-03-14
If I try to use any other package or software management tool this is what it tells me, basically I think that ubuntu tweek has taken over and will not allow anything to update the system any more pls help?

terminal:

giannisdesk@giannisdesk-CM5571:~$ sudo apt-get update
[sudo] password for giannisdesk: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/

software center
Check if you are currently running another software management tool, e.g. Synaptic or aptitude. Only one tool is allowed to make changes at a time.

pretty  much same fore synaptic

---

### Post by matthewbpt on 2011-03-14
Go to the terminal and type

```
sudo lsof /var/lib/dpkg/lock
```

This should tell you what process is locking dpkg. Post th output here so we can help you.

---

### Post by flipper T on 2011-03-14
what makes you think that this has anything to do with ubuntu tweak ?

if you do have tweak open at same time...try closing it

---

### Post by gcomito11 on 2011-03-16
> **matthewbpt said:**
> Go to the terminal and type
 
```
sudo lsof /var/lib/dpkg/lock
```
 
This should tell you what process is locking dpkg. Post th output here so we can help you.
 
 
I will post as soon as I get a chance, stuck at work and forgot to subscribe to the thread to get notificaion that I had a response, thank you for the help.

---

### Post by gcomito11 on 2011-03-16
> **flipper T said:**
> what makes you think that this has anything to do with ubuntu tweak ?
 
if you do have tweak open at same time...try closing it
 
This started as soon as I utilized tweak to get a few applications instead of using software manager or synaptic like usual.  So really I do not know I just suspect, and we will find out tonight if at all possible.
 
And even if closed it happens.
 
Thanks for taking a look at my thread by the way.

---

### Post by gcomito11 on 2011-03-16
> **matthewbpt said:**
> Go to the terminal and type

```
sudo lsof /var/lib/dpkg/lock
```This should tell you what process is locking dpkg. Post th output here so we can help you.

strange

giannisdesk@giannisdesk-CM5571:~$ sudo lsof /var/lib/dpkg/lock
[sudo] password for giannisdesk: 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/giannisdesk/.gvfs
      Output information may be incomplete.
giannisdesk@giannisdesk-CM5571:~$

---

### Post by gcomito11 on 2011-03-16
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the list directory


thiis is no happening from tweak so I dont think it is tweak any longer.  this is very strange please help me.

---

### Post by gcomito11 on 2011-03-16
update manager now tells me the same thing but here are the details

The package indexes are currently changed by apt-get.

---

### Post by gcomito11 on 2011-03-16
so very sorry for all the time spent by those in the ubuntu forums that try to help those of us that have no idea.

I restarted and now everything works just fine, I downloaded a new ap through tweak and it didn't tell me I needed to restart for it to take effect so I am assuming that was the problem.

Wow I feel a little dumb.

---

