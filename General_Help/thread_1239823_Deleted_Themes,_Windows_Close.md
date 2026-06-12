---
title: "Deleted Themes, Windows Close"
date: 2009-08-13
forum: General Help
---

### Post by Nate Shoffner on 2009-08-13
Let me start off saying that what I did was stupid.  I realise this now.  I was going through themes that had came pre-installed with Ubuntu Jaunty.  I am no expert with Ubuntu, obviously.  I started using "sudo chown nate /usr/share/themes/ThemeFolder" to give permission to delete the folders.  Eventually, I deleted one that screwed up my current theme.  I tried to go to System > Preferences > Appearence and it closes the windows within a second.  I feel so stupid for doing this.  I've restored the folders back to the original directory but the problem still exists.  Another wierd thing is, when I try to open another tab in Mozilla Firefox, it automatically closes that too. :confused:  Can someboy please steer me in the right direction so I can get everything back to normal.  Thank you!!

---

### Post by Nate Shoffner on 2009-08-14
UPDATE:  I managed to fix the problem.  Just incase anybody has this problem in the future, this is what I did:

I opened the terminal and typed

```

sudo apt-get install gtk-theme-switch
switch2

```I then changed the theme to Human and now everything works again.  Man, I feel so dumb about this.  But we learn from our mistakes. :P

---

### Post by CatKiller on 2009-08-14
> **Nate Shoffner said:**
>  I started using "sudo chown nate /usr/share/themes/ThemeFolder" to give permission to delete the folders.

Don't change the permissions on system folders. It leads to breakage. If you **have** to do things to system folders, do it as root.

You'll probably find ```
gksudo nautilus
``` useful to run a file browser as root.

---

### Post by Nate Shoffner on 2009-08-14
Would all of this cause problems with new themes being installed?  None of them appear as they should.

---

### Post by CatKiller on 2009-08-14
> **Nate Shoffner said:**
> Would all of this cause problems with new themes being installed?  None of them appear as they should.

Probably. Deleting system files willy-nilly isn't recommended.

If you can remember what you deleted, you could re-install the packages that created those files and then remove them through the package manager. That way, if a package needs them to be there, it will bring them in as a dependency.

---

### Post by Nate Shoffner on 2009-08-14
Any chance you could tell me where I could find those?  The only system files that I had deleted were the default themes that came with Ubuntu.

---

### Post by CatKiller on 2009-08-14
Not really, because I don't know exactly which ones you deleted (or which ones are in a default install, for that matter - mine was over four years ago).

Establishing which themes don't "appear as they should" would probably be your first step to finding out what's missing. Then you might see what they have in common - theme engines, potentially.

---

### Post by Nate Shoffner on 2009-08-14
I'll use the theme Dark Room as an example.  It was pre-installed with Ubuntu.  Would deletion of that affect themes that are added later on?

---

### Post by CatKiller on 2009-08-14
Only those that use the DarkRoom borders, colours, or controls.

---

