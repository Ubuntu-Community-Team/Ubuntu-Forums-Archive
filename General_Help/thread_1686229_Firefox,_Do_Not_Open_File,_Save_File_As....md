---
title: "Firefox, Do Not Open File, Save File As..."
date: 2011-02-12
forum: General Help
---

### Post by light-vessel on 2011-02-12
I have spent many weeks trying to find the answer to this:

I use firefox on Ubuntu Lucid. When I click on a video or archive file (eg. mpeg, rar...) I NEVER want to open it with an application. I always want to save the file to a location of my choice. Firefox always asks me what I want to do with the file. It has the option "always do this" but it doesn't let me check this box for "save file as..."

I have tried looking through about:config and one or two settings look like they should do this, but they don't. In Firefox preferences > applications, rar is not listed and the only video file type mentioned is "Windows Media Video".

Other people who have asked similar questions want programs to open files, but very few answers can be found, so I can't even work out how to do the opposite for what I want.

---

### Post by labinnsw on 2011-02-13
Did you see [this post]("http://ohioloco.ubuntuforums.org/showpost.php?p=9336484&postcount=3") in [this thread?]("http://ohioloco.ubuntuforums.org/showthread.php?t=1489479")

One cause could be a corrupted profile which you can fix using [one of these methodes]("http://www.webgapps.org/firefox/fixing-corrupted-profiles")

---

### Post by light-vessel on 2011-02-16
I can't find an answer there. I don't think firefox is corrupted. I think this is a default setting when it's installed, but I just don't know how to change it.

---

### Post by labinnsw on 2011-02-16
> **light-vessel said:**
> I think this is a default setting when it's installed,

I doubt that strongly. If that were the case, I believe myself and other firefox users would have encountered the problem before. I am sure countless posts  would have been written about it. I also know that the default setting is to ask what you want to do with the file and to save it to the downloads folder if you choose to save without specifying a destination.

If you are not convinced, you could also try editing firefox preferences.
Edit>>Preferences>>General
and
Edit>>Preferences>>Applications

---

### Post by light-vessel on 2011-02-19
I have already combed through all the preferences and the about:config. Firefox behaved the same way when I used it on Windows. This isn't something that can be found in the simple preferences panel.

I repeat: it asks me what I want to do with each file, but it just doesn't give me the option of telling it to always save to a location of my choice.

---

### Post by WorMzy on 2011-02-19
I get the option:
[IMG]http://img254.imageshack.us/img254/7650/20110219073318343x357sc.png[/IMG]

I'm using Unbranded Fx v3.6.13. I doubt that DownloadThemAll! has any effect on this, beneficial or otherwise, but you could try installing it and seeing if it helps.

---

### Post by labinnsw on 2011-02-19
> **light-vessel said:**
> I have already combed through all the preferences and the about:config. Firefox behaved the same way when I used it on Windows. This isn't something that can be found in the simple preferences panel.

I repeat: it asks me what I want to do with each file, but it just doesn't give me the option of telling it to always save to a location of my choice.

That is why my initial response was to ask you to fix your firefox profile but you then said > **light-vessel said:**
> I think this is a default setting when it's installed, but I just don't know how to change it. So I tell you how to change it.

---

### Post by grizzler on 2011-02-19
> **light-vessel said:**
> I repeat: it asks me what I want to do with each file, but it just doesn't give me the option of telling it to always save to a location of my choice.

I had the same problem with tar.gz files on a particular site. Couldn't get Firefox to always download them, no matter what I tried, including starting with a new profile. I ended up manually editing the mimeTypes.rdf file in the profile folder. It's not exactly clearly layed out and you need to know what to change and where (in my case, that was adding the line **NC:fileExtensions="gz"** to the "urn:mimetype:application/gzipped-tar" entry).

The real problem here was the site itself, though. It sent the wrong Content-Type header with these files.

---

