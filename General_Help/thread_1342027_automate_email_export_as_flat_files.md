---
title: "automate email export as flat files"
date: 2009-11-30
forum: General Help
---

### Post by bfuzze on 2009-11-30
I'm trying to find a way to automate an export of emails as flat text files. 

I spent a few hours yesterday playing around with some options for exporting from hotmail.  I'm not bound to hotmail, it's just where I started.  I've read it's a lot easier to export from gmail, so I'm moving in that direction in terms of an email src.  I want to grab the emails and bring them down to my local computer for parsing.

Incidentally, I'm working on a variety of platforms Ubuntu 8.04/9.04 and WinXP.

What I've done so far... 
- I found a lot of posts about gotmail, hotway, getlive, but I had little luck with these as they are older scripts.  They're in the 8.04 repositories, but the scripts are no longer compatible with hotmail systems based on what I can tell.  
- I also played around with evolution.  I successfully connected evolution and hotmail, but the flatfiles can only be found in the cache and the file names are encoded.  Plus automating this would be mean hacking evolution which is not something I'm interested in.  
- I also played around with some other perl scripts and fetchmail.  
- I even broke down and tried Outlook Express, toying with some possibilities there.  

Perl seems to be the preferred method of POP3 comm, but I haven't found a script that works for hotmail, which is why I'm starting to think maybe I should be looking at a different source client, like gmail.

I'm just curious how some of the other members might approach such a problem.

Any suggestions/insight appreciated.

---

### Post by Bag-O-Stuff on 2009-11-30
Try Thunderbird.  It stores it's files in a sensible manner where you can find them and then they are in a simple mbox format.  You can simply copy them off.  I use it to automate SpamAssassin training and it works great!

If you are looking to be truly automatic where you don't even open Thunderbird, I'd try fetchmail and a simple local mail server that stores in an mbox format as well.

---

### Post by bfuzze on 2009-11-30
Thanks, I'll give this a shot.

---

