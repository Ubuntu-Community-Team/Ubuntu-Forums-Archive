---
title: "Evolution 2.32 Unix Mail file How?"
date: 2011-12-22
forum: General Help
---

### Post by jerome schatten on 2011-12-22
Evolultion 2.28 and earlier produced a Unix format mail file in /home/xxx/.evolution/mail/local/Inbox.sbd iirc.  The version of Evolution that comes with 11.04 (2.32) seems to do no such thing -- at least I can't find it by drilling down the /home/xxx/ directory.

What to do? I need the Unix files to feed my archiving programme that archives posts for my websites.  Abandon Evolution for Thunderbird? or have I just not found the files yet?

Any insight on this would be appreciated.
Jerome

---

### Post by dcstar on 2011-12-22
> **jerome schatten said:**
> Evolultion 2.28 and earlier produced a Unix format mail file in /home/xxx/.evolution/mail/local/Inbox.sbd iirc.  The version of Evolution that comes with 11.04 (2.32) seems to do no such thing -- at least I can't find it by drilling down the /home/xxx/ directory.
........

The path to the files has simply changed with this new version of Gnome/Unity. Do a web search for the new folder path.

---

### Post by jerome schatten on 2011-12-22
> **dcstar said:**
> The path to the files has simply changed with this new version of Gnome/Unity. Do a web search for the new folder path.

OK... the mail files have been found. Thanks... now on to the next question:

I put my .evolution folder from my Ev. 2.28 (U9.1) machine into my home directory on
my U.11.04 machine. 

Indeed Ev. 3.2 found the folder and put all my old mail files and folders into 
~/.local/share/evolution/mail/local/Inbox.sbd.  

So now my question is: How to tell evolution on the 11.04 machine to take these folders and display them in Ev.3.2?

jerome

---

### Post by jerome schatten on 2011-12-22
Cancel my last... got it all working. I clicked on something in Evolution (I know not what) and BINGO -- all the stuff from my previous Inbox (my old Inbox.sbd) appeared. Magic!  I was able to import my previous Sent mail file using Import from the Ev. File menu. So all is well and everything seems to work.

That's it... If anyone else is travelling this path, the stuff you want is in:

home/yerhomefolder/.local/share/evolution/mail/local

I'm gonna close this thread as solved.
jerome

---

