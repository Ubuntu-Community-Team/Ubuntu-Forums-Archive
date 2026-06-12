---
title: "Where does the RAM go?"
date: 2006-04-23
forum: General Help
---

### Post by hizaguchi on 2006-04-23
A couple weeks ago I got the itch to try a different distro, so I took Arch Linux for a spin.  I don't normally install Gnome because it eats up so much memory (about 100 megs) in Ubuntu, but everything else was going so fast I gave it a try on Arch.  Well, it was obviously faster partially because of the i686 optimization, but it also used MUCH less memory (about 60 megs).  Which leads me to my question, where does that extra memory go?

I've used BUM to turn off everything that doesn't seem absolutely necessary and I've even taken the update notifier out of my session.  I know I can further reduce my usage by getting rid of Nautilus (which I'm considering) and Metacity (which I actually like), but I'd really like to figure out what's different about Arch's Gnome that saves nearly 50% on ram usage... and how I can make Ubuntu's Gnome do the same.

---

### Post by testube_babies on 2006-04-23
Open up a terminal and type the command 'top'.  This will show you how your RAM is being used at any particular moment.

---

