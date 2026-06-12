---
title: "Exit GUI?"
date: 2010-01-28
forum: General Help
---

### Post by Overcast32 on 2010-01-28
Question.. I'm using 9.04 server for a Content Filtering System with Dansgaurdian.

I want the GUI (Gnome) so I can use the machine on occasion for more than just 'server' tasks, so I loaded up the GUI. 

But two things:

How do I keep it from loading the GUI by default?
Then after that, how would I load up the GUI

*And potentially exit it without rebooting? And of course, leave other services like DNS/Squid/Dansguardian running?

Thanks in Advance!

---

### Post by c0mput3r_n3rD on 2010-01-28
I know to start and stop the gnome display manager the command is:
```

sudo etc/init.d/gdm start

```
and of course you would just type stop to stop it.  And if you're working in the GUI already you can just press  CRTL+ALT+[F1-F6]  (F7 is to return).

---

### Post by Overcast32 on 2010-01-28
> And if you're working in the GUI already you can just press CRTL+ALT+[F1-F6] (F7 is to return).

Does that actually unload the GUI and not just give a full screen terminal?

This PC that it's running on isn't the fastest in the world, so if I don't need the GUI, I want to just unload it completely. 

Thanks for the quick reply

---

### Post by Overcast32 on 2010-01-28
Ok, think I got it - do the CTRL+F1 then unload GDM.. 

That right? :)

---

### Post by t4thfavor on 2010-01-29
> **Overcast32 said:**
> Ok, think I got it - do the CTRL+F1 then unload GDM.. 

That right? :)

There is a way to take gdm out of the startup rc.x, I just have no idea what to do. Look into disabling auto start for services, and I bet you could find it.

maybe set the default runlevel to 4, which I believe is text mode only, where 5 is gui, and 6 is reboot. 

at least that's what I remember from school.

---

### Post by Overcast32 on 2010-02-01
Actually - I found that you can run "sysv-rc-conf"... 
And tell it to not load GDM :)

But thanks for that info - another file name to poke around at ;)

---

