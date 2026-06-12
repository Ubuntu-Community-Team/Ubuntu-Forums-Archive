---
title: "Buggy Cairo Dock after update"
date: 2010-01-15
forum: General Help
---

### Post by cespinal on 2010-01-15
Hello guys, 

Does this has happened to you since the last updates?:

Cairo dock runs okay, but after a while, all the accessories that should open nautilus windows (shortcuts, recycle bin, quick browser) stop working, being unable to open anything!. 

closing Cairo and launching it over solves the problem... but I don't wanna do that every hour or so!. 

any hints?

Also, enjoy some brushie :)

---

### Post by fabounet on 2010-01-15
> since the last updates
there has not been updates of CD since almost 2 months (except if you're on the development version), so I guess you're talking about some Ubuntu updates ?
then it would sound like a bug in *gvfs* (or maybe nautilus). it would probably worth reporting it to the devs.

---

### Post by snowman63 on 2010-01-23
I have the same issue. I've found PPA updates for Nautilus and Cairo-dock and nothing seems to work.
By the same token the gnome-panel won't go away even after going into the  gconf-editor. So I made it as small as possible and have it auto-hide below the cairo-dock. The panel only has one Icon on it to restart cairo-dock when it stops working and I have to shut it down.

---

### Post by fabounet on 2010-01-24
what if you deactivate the applet and reactivate it ?
is there any debug output in the terminal ?

---

### Post by cespinal on 2010-01-24
there should be a way to track any crashes

---

### Post by omkardanke on 2010-01-31
I seem to be having the same problem with cairo dock. It works fine initially when it is run. But after some time when we have not touched the dock, it stalls...

So have to kill it and rerun it. that works, But only for the next 5 mins. Also i run the program from the terminal. It doesn't give any error message before it stalls.

I guess it's back to the old panel for me.

---

### Post by fabounet on 2010-01-31
consider updating to the latest version (2.1.3) available on Launchpad

---

### Post by robertrose6 on 2010-01-31
> **fabounet said:**
> consider updating to the latest version (2.1.3) available on Launchpad

Can you please let me know how to do that. And if I do that will I have a more themes to choose form?

---

### Post by robertrose6 on 2010-01-31
> **robertrose6 said:**
> Can you please let me know how to do that. And if I do that will I have a more themes to choose form?

Ok I found out to get themes. You have to run this in the terminal

cairo-dock -S themes.cairo-dock.vef.fr

and while this is running go to manage themes in cairo dock. This will give you the list of themes. 

But I still am not sure how to update Cairo Dock

---

### Post by fabounet on 2010-02-01
you can do that on launchpad, we have a PPA (personnal repository)
[http://launchpad.net/cairo-dock]("http://launchpad.net/cairo-dock")

---

