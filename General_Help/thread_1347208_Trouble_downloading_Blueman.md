---
title: "Trouble downloading Blueman"
date: 2009-12-05
forum: General Help
---

### Post by bmman on 2009-12-05
I want to use the Bluetooth capability in my Dell Netbook (running Ubuntu 8.04) and apparently need to download Blueman. This, I am having trouble doing. The following error message resulted

E: Malformed line 15 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.ed

Can anyone point out what I'm doing/not doing wrong??

---

### Post by zvacet on 2009-12-06
In terminal type

```
cat /etc/apt/sources.list
```

and post output here.

---

### Post by 3rdalbum on 2009-12-06
When you add repositories to your system, DON'T manually edit the /etc/apt/sources.list file; it's too easy to make a mistake. Instead, use the Software Sources program, it makes sure that the line you've typed is correct before adding it to the sources list.

When people say "Open /etc/apt/sources.list and add this to the file", just go to Software Sources, click the Third Party tab, click the Add button and paste each line in.

---

### Post by bmman on 2009-12-06
> **zvacet said:**
> In terminal type

```
cat /etc/apt/sources.list
```

and post output here.

OK, I typed "cat /etc/apt/sources.list" into the terminal. This dropped the cursor down to the next line, but I wasn't asked for my password (as when I entered "sudo getit /etc/apt/sources.list") 
and therefore was not directed to the sources.list page. In other words, there was no post.
When I typed in the sudo getit..... line I was directed to the sources.list page, which had the following post on it:

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted 
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted 
 
deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted 
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted 
 
deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted 
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted 
 
deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted 
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted 
 
deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted 
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted

I had tried entering deb [http://ppa.launchpad.net/blueman/ppa/ubuntu](http://ppa.launchpad.net/blueman/ppa/ubuntu) hardy main in a different way, which brought up the error message. I have since backed that line out, and now the error message is gone. But I still can't seem to get Blueman to Save.

---

