---
title: "How to set File Roller as Default archive app?"
date: 2010-03-10
forum: General Help
---

### Post by Jheric on 2010-03-10
Hey, I was messing with Openbox, LXDE, and Pekwm a couple days ago to see if I liked any of them, but I ended up coming back to gnome.

But it seems that, somehow, some of my preferred apps settings got wiped during this process.

The most annoying one, is I have no default application for archives (zip, tar.gz, etc). I can tell Ubuntu to "Open With..." and that works... but it doesn't stick.

How can I return this back to normal Ubuntu behavior?

**UPDATE: It appears that nearly ALL my preferred application settings are gone. Pretty much everything except couple filetypes show up with the standard "file" icon and won't open unless I use "open with".**

---

### Post by fragos on 2010-03-10
Rather than Open with select Properties and add File Roller on the Open with tab. This will change Open with for all files of a particular mime type. The application you may want is called "Archive Manager". That is the Ubuntu Gnome default.

---

### Post by Jheric on 2010-03-10
> **fragos said:**
> Rather than Open with select Properties and add File Roller on the Open with tab. This will change Open with for all files of a particular mime type. The application you may want is called "Archive Manager". That is the Ubuntu Gnome default.

Unfortunately, this seems to be missing from the properties area on my files. Is there a way to re-enable this?

---

### Post by Jheric on 2010-03-10
Ack!... I just realized that that's not even nautilus! That's PCMan! What a mess I caused...

It seems that firefox opens PCMan by default now, instead of nautilus. And PCMan is ignorant of all my application settings. I suppose the solution would be just to dump PCMan... firefox should use nautilus if PCMan is gone, right?

---

### Post by fragos on 2010-03-10
> **Jheric said:**
> Ack!... I just realized that that's not even nautilus! That's PCMan! What a mess I caused...

It seems that firefox opens PCMan by default now, instead of nautilus. And PCMan is ignorant of all my application settings. I suppose the solution would be just to dump PCMan... firefox should use nautilus if PCMan is gone, right?

If not goto about:config in Firefox and change PCMan to Nautilus where ever you find it. I've no personal experience with using PCMan. If all else fails delete ~/.mozilla and start over with with a clean Firefox.

---

### Post by mechro on 2010-03-10
You may have set PCman to manage your Desktop instead of Nautilus...

In PCman go to **Edit > Preferences > Desktop** and untick the item **Manage the desktop and show file icons**... that's if it happens to be ticked, of course.

---

### Post by Jheric on 2010-03-10
Thanks for the responses. I can't find nautilus or pcman mentioned in Firefox's about:config. And I can't scratch this profile of Firefox since the data is all work-related.

I think I can  get it straightened out from here though... thanks for the help guys!

---

