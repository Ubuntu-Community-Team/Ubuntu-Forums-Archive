---
title: "startup script in serial"
date: 2009-10-28
forum: General Help
---

### Post by nightfrost on 2009-10-28
I'm trying to write a small init script that rsyncs two directories just after the disks are mounted (but before X starts up). Linking to it from /etc/rc2.d/S99myscript works, but since scripts are run in parallel, the syncing occurs while the system continues to boot up.

Is there a way to force a script to not be run in parallel?

---

### Post by Giblet5 on 2009-10-28
Yes, but it's almost certainly not what you really want to do.

Anytime you want to override the default behavior, which has been very VERY carefully thought-through by thousands of smart people, an alarm bell should go off behind your left ear...

What are you trying to accomplish?

---

### Post by nightfrost on 2009-10-28
> **Giblet5 said:**
> Yes, but it's almost certainly not what you really want to do.

Anytime you want to override the default behavior, which has been very VERY carefully thought-through by thousands of smart people, an alarm bell should go off behind your left ear...

What are you trying to accomplish?

I totally see your point, and I completely agree too :)

But what I'm trying to do isn't, shouldn't, and will never be a default feature of Ubuntu. This is what I'm trying to accomplish:

I have Ubuntu installed on my laptop's internal drive. I also have  Ubuntu installed on an external drive. I mainly use the internal drive of the laptop of course, but sometimes, I will boot up from the external drive instead. Now, when booting up from the external drive, I want the home dir on the external drive be an exact copy of the home dir I have on my internal drive; this should be accomplished with a simple rsync command. Conversely, on shutdown, I want everything synced the other way around (this part is no problem).

The problem is, as you might have guessed already, the sync starts properly, but continues when my DE is up and running, which sort of messes things up. Ideally, the boot up would take a pause while the sync is underway, and should resume when the syncing is done.

If you have a better idea of how I should accomplish this, I'm all ears :)

---

### Post by Giblet5 on 2009-10-28
Make a copy of /etc/passwd.

Make the copy's mode and ownership match the original.

Edit out your username from the copy.

Use a script from rc.local: ```
mv /etc/passwd /etc/passwd-
cp /etc/passwd.copy /etc/passwd
rsync -aurptd /media/MyBook/home/bob /home/bob/
mv /etc/passwd- /etc/passwd
```

Now you can't log in until the sync is done.

You better add another admin user in case your system crashes during that sync... ;)

---

### Post by QLee on 2009-10-28
> **nightfrost]I have Ubuntu installed on my laptop's internal drive. I also have  Ubuntu installed on an external drive. I mainly use the internal drive of the laptop of course, but sometimes, I will boot up from the external drive instead. Now, when booting up from the external drive, I want the home dir on the external drive be an exact copy of the home dir I have on my internal drive said:**
> 

You might want to investigate the "unison" software since you say the external is always connected.

[QUOTE=nightfrost]The problem is, as you might have guessed already, the sync starts properly, but continues when my DE is up and running, which sort of messes things up. Ideally, the boot up would take a pause while the sync is underway, and should resume when the syncing is done.

Show us your script.

---

### Post by nightfrost on 2009-10-28
That's a good one, thanks!
I'll give this a try.

---

### Post by nightfrost on 2009-10-28
Works like a charm. Thanks :)

---

