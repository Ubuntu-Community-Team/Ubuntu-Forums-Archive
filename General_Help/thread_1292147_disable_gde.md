---
title: "disable gde"
date: 2009-10-15
forum: General Help
---

### Post by Neezer on 2009-10-15
I have been looking for a way to disable my gnome desktop environment via ssh. I have 9.04 desktop installed and am away from home for a about 3 weeks. I want to do some work on things, but I just don't need the desktop environment running.

I am also going to need to know how to turn it back on when I get home. 

I would love to be able to eventually keep it off all the time as the unit at home is going to be a server.

I remember seeing some init 1,2,3,4,5,6 codes that I think would work, but I can't pull up the thread.

---

### Post by SPr on 2009-10-15
While sitting at the desktop you would do this:
Ctrl+alt+f1
log in then
```

sudo /etc/init.d/gdm stop

```

I don't know whether that can be done remotely. I've never logged into a remote PC before.

---

### Post by Neezer on 2009-10-15
> **SPr said:**
> While sitting at the desktop you would do this:
Ctrl+alt+f1
log in then
```

sudo /etc/init.d/gdm stop

```

I don't know whether that can be done remotely. I've never logged into a remote PC before.

I am sure that I could do your code to stop it from remotely, but will i be able to start the gdm remotely as well? would:

```

sudo /etc/init.d/gdm start

```

Would that work remotely as well?

---

### Post by Johnny B on 2009-10-15
i just tried it and after i shut down gdm over ssh my laptop hung on "checking battery state" and i could not reconnect, it needed to manually rebooted.

---

### Post by Neezer on 2009-10-15
well, the laptop is the computer I'm working on right now...the server unit at home that I will be shutting the gde down on is a plain old box....so it shouldn't have a battery. 

Still waiting on confirmation for this...it sure would suck to not be able to work on this for 3 weeks.

---

### Post by CatKiller on 2009-10-15
> **Neezer said:**
> I am sure that I could do your code to stop it from remotely, but will i be able to start the gdm remotely as well? would:

```

sudo /etc/init.d/gdm start

```Would that work remotely as well?

Just worked for me. Since you're there with both machines handy, you'll probably want to check it yourself.

EDIT: Don't forget to forward X connections over SSH if you're planning on using any graphical applications remotely having started GDM.

---

