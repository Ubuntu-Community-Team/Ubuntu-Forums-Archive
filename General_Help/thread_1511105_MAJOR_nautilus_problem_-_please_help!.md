---
title: "MAJOR nautilus problem - please help!"
date: 2010-06-16
forum: General Help
---

### Post by frogotronic on 2010-06-16
I have a wierd, and potentially catastrophic problem with my Karmic install.  On the Open With menu I ALWAYS for every file have the option to Open With "Nautilus" (see screenshot).

I have tried to poke around and figure out how to REMOVE the nautilus option, which seems to be VERY hard to do.  I was following this post: [http://ubuntuforums.org/showthread.php?p=2161195](http://ubuntuforums.org/showthread.php?p=2161195)

This is the code for nautilus.desktop from my ~/.local/share/applications

```
[Desktop Entry]
Encoding=UTF-8
Exec=nautilus --no-desktop %U
Hidden=true
Icon=folder-open
**MimeType=x-directory/gnome-default-handler;x-directory/normal;inode/directory;application/x-gnome-saved-search;**
Name=Open Folder
NoDisplay=true
OnlyShowIn=GNOME;
StartupNotify=true
Terminal=false
TryExec=nautilus
Type=Application
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Product=nautilus
X-GNOME-Bugzilla-Version=2.28.1
X-Ubuntu-Gettext-Domain=nautilus
```

Should I delete the bolded MimeType?  I don't think would be a good idea.

Can anyone please help?

Thanks,
CH

---

### Post by dino99 on 2010-06-16
i've no experience with this but "Hidden=true" does make the job itself

forgot to say you might use gconf-editor instead to set your prefs

---

### Post by doas777 on 2010-06-16
backup your file first, but it should be safe to mess with. the inode\directory token seems a little out of place. just make sure you are familiar enough with the cli to undo your change if you lose the ability to open stuff in nautilus.

---

### Post by frogotronic on 2010-06-16
> **dino99 said:**
> i've no experience with this but "Hidden=true" does make the job itself

Explain this statement - it doesn't make sense to me.

> forgot to say you might use gconf-editor instead to set your prefs

Where would I find the relevant settings?

---

### Post by frogotronic on 2010-06-16
> **doas777 said:**
> backup your file first, but it should be safe to mess with. the inode\directory token seems a little out of place. just make sure you are familiar enough with the cli to undo your change if you lose the ability to open stuff in nautilus.


I'm pretty good with CLI; what is a "token" and how does that work?

---

### Post by doas777 on 2010-06-16
> **cement_head said:**
> I'm pretty good with CLI; what is a "token" and how does that work?
sorry, it's a programmer term.
the line you had in bold, is several "tokens" of text, divided by semicolons. a token is just a discrete bit of data that is in a string with other data. think of each word in a sentence as a token, and the sentence as the string itself.

 I'm suggesting that you try removing the "inode\directory" token so your line woudl then look like:
```

MimeType=x-directory/gnome-default-handler;x-directory/normal;application/x-gnome-saved-search;

```

no idea if that is the correct answer, just the first thing I would try (after backing the file up, of course).

---

