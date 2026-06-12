---
title: "Are you also having problems with &quot;egg_desktop&quot; messages during upgrade?"
date: 2006-06-16
forum: General Help
---

### Post by magnusbb on 2006-06-16
Hello everyone,

over the last few days this problem is getting more and more annyoing, most of all, simply because it's coming up during (nearly) every update of the system - of which there are recent these days.

My message is simply during an apt-get session:
"** (process:19735): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed"

I found some answers in this thread:
[http://www.ubuntuforums.org/showthread.php?t=186609&highlight=lacks+MimeType+key](http://www.ubuntuforums.org/showthread.php?t=186609&highlight=lacks+MimeType+key)

To check if the problem also is present on your machine, try the following:

```
cd /usr/share/applications
sudo update-desktop-database -v
```

If you're getting messages like...
```
File '/usr/share/applications/gnome-sound-recorder.desktop' lacks MimeType key
```

... well, welcome to the club!

The problem with these files, is, according to the mailing list posts, that there are duplicate entries inside the files, and that they are causing these troubles. I counted around 70 files affected by this on my computer, and the list is growing...

Can someone help me out? Do I have to edit every single file?

Magnus

UPDATE: In some of my files, not duplicates, but invalid entries are causing the problems. In most of the files it has to do with the internationalization "comments" in every language, associated with these files.

UPDATE II: I have tracked the problem, on my computer, down to the following: it has to do with a locale called "sr@Latn", which causes the problems, by applying an invalid formatting to the .desktop-file.

---

### Post by erdalronahi on 2006-08-29
Hi, I also have an unusual locale (ku), and I have the same errors. Can you explain a little more what the problem with the ".desktop" files is?

---

