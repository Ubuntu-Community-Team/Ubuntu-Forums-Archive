---
title: "My panel and desktop items disappeared!!!"
date: 2009-08-06
forum: General Help
---

### Post by Topher88 on 2009-08-06
Ok, so I was working with Compiz and Cairo dock in Ubuntu, and I did SOMETHING but I have no idea what, and BAM.  My Cairo Dock and my gnome panel just vanish.  The only thing left is my "computer" icon.  I think "hmmm...  Okay, maybe Cairo Dock accidently got shut down," so I Alt + F2 to bring it back up, type in the command, and it acts like it's already running.  I do the same thing for Firefox; type in the command, and nothing happens.  I restarted thinking that maybe I just did something temporary, but nope...  It boots back up with no visible gnome panel and no visible ANYTHING accept for the "computer" icon.

So now I have a blank screen with no panel and apparently NO working applications...  WTF?  I have no idea what I did or how to get it back...  I was working with Compiz and Cairo to try and get Cairo applets to show up in the Compiz widget layer...  I right clicked something, that's all I know, and then everything was GONE.

Please, please, PLEASE help me!!!

---

### Post by Anxious Nut on 2009-08-06
to bring back your desktop items try: Alt+F2 then type ```
nautilus
``` and hit the enter

my advice, log out and then log in again, i hope i helped

---

### Post by Topher88 on 2009-08-06
> **Anxious Nut said:**
> to bring back your desktop items try: Alt+F2 then type ```
nautilus
``` and hit the enter

my advice, log out and then log in again, i hope i helped

Tried rebooting...  No good.  I'll try the Nautilus thing

Nope, nautilus doesn't work...  does the same as everything else; acts like it's running, but i can't see it.

---

### Post by Topher88 on 2009-08-07
Any ideas???

Please, I need my desktop back!!!!!

---

### Post by synapsys on 2009-08-07
Check this out.

[http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)

---

### Post by Topher88 on 2009-08-07
> **synapsys said:**
> Check this out.
 
[http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)
 
Cool, that worked... Except now I have to reset all of those settings that were working perfectly fine before. And now my Cairo Dock has a black box around it where it didn't before.
 
But thanks, that's better than nothing!

---

### Post by CatKiller on 2009-08-07
> **Topher88 said:**
>  I was working with Compiz and Cairo to try and get Cairo applets to show up in the Compiz widget layer...

As I understand it, not using it myself, the widget layer is **supposed** to hide everything. Possibly that's what happened to you. Or perhaps you ended up putting *everything* in the widget layer...

> **Topher88 said:**
> And now my Cairo Dock has a black box around it where it didn't before.

If everything's back to defaults then you probably aren't running Compiz. If you aren't using a compositing window manager, then things that are supposed to be transparent become black, since there's nothing else that can be put there.

---

