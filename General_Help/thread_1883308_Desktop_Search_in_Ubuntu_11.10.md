---
title: "Desktop Search in Ubuntu 11.10?"
date: 2011-11-18
forum: General Help
---

### Post by orezero on 2011-11-18
Sorry in advance to you more experienced users; I'm just a desktop user, so I'm barely conversant with the command line, etc. I have just installed Ubuntu 11.10, and I cannot for the life of me figure out how to install and/or configure something that will give me an indexed search of my machine. My needs are complicated by the fact that I need to be able to search several directories on my NTSF partition -- something that Tracker used to do on earlier versions of Ubuntu.

I am having no success in getting Tracker to work with Ubuntu 11.10; the Tracker package does not seem to be installing trackerd anywhere that I, or my system, can find, so I can't seem to get indexing started, going, or autostarting.

If I'm supposed to be using some other means to search with Unity, then I don't know what it is.

Can anyone help me figure out what I need to do in order to have a working GUI-based search client on my machine?

Thanks in advance for any help that anyone can give me.

---

### Post by mikewhatever on 2011-11-18
You need to install 'tracker-gui' to get the graphical frontend. Tracker itself doesn't seem to have a graphical user interface.

---

### Post by orezero on 2011-11-19
> **mikewhatever said:**
> You need to install 'tracker-gui' to get the graphical frontend. Tracker itself doesn't seem to have a graphical user interface.

Thanks, Mike --

-- But Tracker GUI is installed. My problem is that Tracker doesn't seem to do anything once I've told it which directories to index. In every previous version of Ubuntu I've used, the Tracker daemon, trackerd, would have to be running for Tracker to do anything. But now, once I've installed the Tracker packages, I can't seem to find trackerd anywhere so that I can assign it as a startup item.

---

### Post by timothyM on 2011-11-23
I had a similar problem with tracker not performing any indexing. If I ran tracker-control, I would get the output of:


```
Store:
23 Nov 2011, 21:17:09:  &#10003;     Store                 - Idle 

Miners:
23 Nov 2011, 21:17:09:  &#10007;     File System           - Not running or is a disabled plugin
23 Nov 2011, 21:17:09:  &#10007;     Applications          - Not running or is a disabled plugin
23 Nov 2011, 21:17:09:  &#10007;     E-mails               - Not running or is a disabled plugin
```

Playing around with the config, and re-installing the tracker-miner-fs package didn't change the status. Turned out all I needed to do was run:

```
tracker-control -s
```

Now my tracker is happily indexing my fs, and giving me results in the search.

---

### Post by bailewen on 2012-01-28
Similar issue here. 

I have tracker installed, the gui is installed and tracker-control reports that it's indexing. 

Just can't figure out any way to use it to search for anything. When I laucnch the gui all I get is indexing options. How do you get an actual search window?

---

### Post by sgage on 2012-01-29
I've had very good results with Recoll (it's in the repos). You can tell it what directories to index, including those on your ntfs drive (I dual boot, and most of my archives are on the ntfs partition). It is capable of indexing many kinds of documents given the appropriate "helper" apps. I install antiword (for Word docs) and libwpd-tools (for my ancient legacy Word Perfect docs), but there are helpers for spreadsheets and pdfs and whatnot.

It is lightning fast in lookups, and seems to be quite thorough/accurate. Gives you a nice preview of found docs.

It does not track changes in docs in realtime - you have to explicitly reindex, but I just tell it to reindex every week or so. You could easily make a little script to make it reindex and make it a cron job for whatever interval you feel you need. Obviously, for searching old existing docs that aren't changing, it's not an issue.

I highly recommend it. I've tried them all, and in my experience and for my needs, it's the best of the bunch.

---

### Post by marnixava on 2012-02-01
Thank you for your recommendation.  I tried a couple of other ones (strigi & tracker) and had issues with both of those.  Recoll suits my needs perfectly. 

> **sgage said:**
> I've had very good results with Recoll (it's in the repos). You can tell it what directories to index, including those on your ntfs drive (I dual boot, and most of my archives are on the ntfs partition). It is capable of indexing many kinds of documents given the appropriate "helper" apps. I install antiword (for Word docs) and libwpd-tools (for my ancient legacy Word Perfect docs), but there are helpers for spreadsheets and pdfs and whatnot.

It is lightning fast in lookups, and seems to be quite thorough/accurate. Gives you a nice preview of found docs.

It does not track changes in docs in realtime - you have to explicitly reindex, but I just tell it to reindex every week or so. You could easily make a little script to make it reindex and make it a cron job for whatever interval you feel you need. Obviously, for searching old existing docs that aren't changing, it's not an issue.

I highly recommend it. I've tried them all, and in my experience and for my needs, it's the best of the bunch.

---

