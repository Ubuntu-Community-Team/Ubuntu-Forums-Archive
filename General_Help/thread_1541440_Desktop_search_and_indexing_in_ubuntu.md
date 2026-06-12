---
title: "Desktop search and indexing in ubuntu"
date: 2010-07-29
forum: General Help
---

### Post by j_zhill on 2010-07-29
Hi,

This afternoon I spent a few hours hoping to find a good desktop search solution for Ubuntu 10.04.

Key criteria:
- on the fly indexing
- ability to add metadata
- indexing of file names and contents

It looks like there are three options:
- Beagle (out of development from Jan 2010)
- Google Desktop
- Metatracker

Problem is, Beagle is no longer being developed, Google looks nasty on my lovely 10.04 (and doesn't allow updating metadata), and metatracker seems to be a bit unreliable.

Does anyone have a good solution?

Have I missed something with metatracker? It doesn't seem to index filenames?? I've been testing with a small collection, and it just doesn't seem to return results for test keywords??

Any suggestions appreciated.

---

### Post by aeiah on 2010-07-29
beagle may no longer be under development, but it's stable and useful. have you given it a try?

---

### Post by HermanAB on 2010-07-29
Funny, the first thing I uninstall on a Linux or Windows system is the damned desktop search, since it is like Emacs and makes any computer slow.

---

### Post by j_zhill on 2010-07-29
@aeiah: Yep gave it a try earlier, and just went back again now. There doesn't seem to be a DO plugin, which I liked with metatracker. Also, I was looking for something that would allow me to add metadata as I go. On the other hand, you're right. It seems to work well and looks stable.

@Herman: Well, yeah. I've been applying the same policy for years and decided that it might be time to have another shot.

If anyone else has another suggestion I would be all ears.

---

### Post by sancho panza on 2010-08-01
I have not used desktop search much, but off late, tracker seems to be better that an year ago. It does seem to index file names. Maybe you need to check the settings or allow it some time to index the files?
Also, you could try the deskbar with metatracker as it provides live results as you search.

A good desktop search tool is really useful on a desktop. I cannot get why Ubuntu is so hesitant to improve an existing one.

---

### Post by radioboy on 2010-09-16
> **sancho panza said:**
> A good desktop search tool is really useful on a desktop. I cannot get why Ubuntu is so hesitant to improve an existing one.

Indeed. It is mandatory for a successful OS.
I've had a good experience using both Beagle and Zeitgeist + Gnome Activity Journal.
The only issue I have had with Beagle is getting "Maximum inotify watch  limit hit", but that's easily solved following the instructions in the  troubleshooting page.

Tracker does lightning fast search on indexed data and allows the use of tags, but I always have problems with it not indexing all my data (sometimes it stalls), sometimes not starting or delaying the login to my session. :(

---

### Post by engine on 2010-09-27
May I extend this thread? which I turned up when searching for "file meta-data". I don't want auto-indexing, but I do want to be able to add a short (256) description to any file's properties and display it in a Nautilus window. File > Properties > Notes adds an intrusive icon in Nautilus, and I can't see any way of adding a Notes column to the display.

Reckon one of you will be able to give me some tips! thanks.

---

### Post by Cherry Cotton on 2011-02-03
I’ve been studying the same problem. Here’s what I’ve tried:

- Regular desktop search, no indexing: I began a full-text search, and 2 days later it was still running (no, not monitoring; it was still turning up results here and there, files I hadn’t touched in ages).

- Tracker. Not only does it not seem to index all my files, but it’s also been inhibiting my computer from suspending. It’s a laptop, and if I put it in my bag without suspending it would likely overheat and fry itself.

- Strigi. It’s indexing my computer right now. It’s main flaw seems to be the lack of... any... UI. That’s rather startling. I installed Catfish, which is supposed to work as a UI for Strigi, and it fails to see that Strigi is running. Deskbar doesn’t see Strigi at all, even though I have the plugin installed (it doesn’t even see the plugin). Meanwhile, Strigi’s own graphical monitoring client displays a blank window when you tell it to display a list of indexed files—a bad sign. Finally, according to the homepage at [http://strigi.sf.net/](http://strigi.sf.net/) , monitoring for new files is “experimental,” while monitoring changes to files is “still under development” and requires you to compile the daemon from scratch. ...! I would think that a filesystem indexer that only indexes files as they were when you first saved them would be a bit... useless.

Tracker and Strigi, and especially Strigi, have the problem of being very opaque as well. Good luck figuring out what it’s doing, whatever UI there is certainly won’t help you. And, if either screw up, which they will, it’s hard to tell where the problem is.

- Beagle. I temporarily activated the old Lucid repositories so I could install this and its associated packages. While the daemon itself works, none of the plugins do at all, resulting in an index of zero files.

So far, I’m totally screwed. I know there’s also Doodle, which I might try after Strigi is finished indexing my computer. I’m worried it might have the same problems, though... it also looks rather simplistic and opaque. Meanwhile, Strigi had indexed over a quarter-million files in an index of over two gigabytes and counting, and I have no way to know if that’s how many files I really have in my home folder, or if it’s following symlinks and got caught in a loop or something. (sigh)

By the way, I use a remote backup service, and after trying all these indexing solutions the backup client began running day and night, “setting attributes” of the files in my remote backup. I’m guessing it’s updating the “file accessed” time of all the files now that I’ve had all these indexers running around searching everything. I’m turning my remote backup off for now, then, until all this gets fixed, so I won’t have to pay for too much remote-backup bandwidth... (sigh)

---

### Post by cjhabs on 2011-02-03
I use recoll after unsuccessfully trying assorted other options - it has worked best for me.
The down side is no automatic indexing, you need to kick it off manually or in a cron.

---

### Post by Pausanias on 2011-02-23
This has been such a sad story. Tracker was used for a while, then it was too unstable so they disabled it. Lack of desktop search is one of the primary things that makes Ubuntu look completely underpowered and weak compared to Mac OS X or Windows 7. In those two OS, desktop search is my **primary** means of navigating the OS. Spotlight/Start, type in something, boom it comes up in at most half a second.

---

### Post by tyler9 on 2011-03-12
> **Pausanias said:**
> This has been such a sad story. Tracker was used for a while, then it was too unstable so they disabled it. Lack of desktop search is one of the primary things that makes Ubuntu look completely underpowered and weak compared to Mac OS X or Windows 7. In those two OS, desktop search is my **primary** means of navigating the OS. Spotlight/Start, type in something, boom it comes up in at most half a second.

  ...found this thread while searching for what I thought would be something simple: a robust desktop search tool.  I don't get it. Lack of something so elementary--why?   Among the millions of Ubuntu users, at least a few have disabilities that make using a computer difficult. To have this additional problem of struggling to simply to find something...it's discouraging. Such a user tends to throw up their hands [if their hands and arms are functioning that day...] and say, forget it--get a Mac or install Windows.

---

### Post by nerdy_kid on 2011-03-12
give Kubuntu a shot.  KDE (which is what Kubuntu runs) comes with Nepomuk -- which allows you not only to index your files (names+content) but to add metadata (tags, etc) to all your files and folders.

---

### Post by tyler9 on 2011-03-14
> **nerdy_kid said:**
> give Kubuntu a shot.  KDE (which is what Kubuntu runs) comes with Nepomuk -- which allows you not only to index your files (names+content) but to add metadata (tags, etc) to all your files and folders.

Thanks for pointer--Good reason to finally try KDE--

---

### Post by nerdy_kid on 2011-03-15
> **tyler9 said:**
> Thanks for pointer--Good reason to finally try KDE--

just make sure you are using the Raster rendering backend and you shouldn't have any of the "lagginess" that KDE4 seems to be famous for.

```

sudo apt-get install kde-config-qt-graphicssystem

```
(maverick only)

you can find the module in system settings.

---

