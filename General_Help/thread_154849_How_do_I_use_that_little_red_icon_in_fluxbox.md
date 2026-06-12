---
title: "How do I use that little red icon in fluxbox?"
date: 2006-04-03
forum: General Help
---

### Post by barebones on 2006-04-03
I recently started fiddling around with fluxbox, and I'm really enjoying it. One thing I really miss from gnome though is that little red icon that pops up if updates are ready. Update Manager works fine in Fluxbox, but it has to be run manually. Is that little red icon part of Gnome itself, or could I run it in the tray in fluxbox? Its pretty easy to get stuff running at startup via the .fluxbox/startup file, but I can't find the name "that icon" or what actually puts it in the tray. Anybody think they could help me out?

---

### Post by antiemptyv on 2006-04-04
You can run "sudo apt-get update" and "sudo apt-get upgrade" to check for and install updates... manually or automatically at startup.

---

### Post by barebones on 2006-04-04
Thanks for the reply antiemptyv, but thats not really what I'm looking for. I can update my system manualy no problem, but I'm looking to migrate whatever program it is that pops up that little red icon in the systray over to fluxbox.

---

### Post by Toxicity999 on 2006-04-04
I understand where your coming from with this... but really whats the point... I know its nice having everything brought directly to your attention when updates are available but it really is a needless vanity for any semi-experienced user... just take that advice and have everythign update automatically, then you dont even need to worry about any interfacign with whatever. No need for the update alert. ( though in dapper that popup is rather hawwt.)

---

### Post by barebones on 2006-04-04
I'm pretty iffy on the idea of automatic updates, especially in linux. I like to at least look through whats going to be updated. That way if something like a new kernel is going to break x I'll be ready for it ;)

---

### Post by barebones on 2006-04-04
I found out that the program that runs that little icon is simply called update-notifier (D'oh, it was right in the session startup information) but it seems to act weird in fluxbox. It'll start, it's icon will flash in the system tray and then dissapear, and will then even show the little baloon that says theres updates. The problem is though, the icon has dissapeared, so theres nothing to click on to start up update-manager. Anyone have an idea what would do this and what might fix it?

---

