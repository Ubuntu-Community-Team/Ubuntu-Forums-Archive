---
title: "what do people use to backup gmail?"
date: 2011-01-02
forum: General Help
---

### Post by bodhidharma on 2011-01-02
Hey folks,

I wonder whether people have experience they are willing to share about gmail backup tools. There's the method of just synchronizing through some mail client on your linux box, but I don't typically use such a client, so I was thinking simply of using a tool.  There are some postings around the 'net about this, but they often seem a year or more old.  Does anyone have recent experience with one they like?  What about the "getmail" approach described here
[http://www.mattcutts.com/blog/backup-gmail-in-linux-with-getmail/](http://www.mattcutts.com/blog/backup-gmail-in-linux-with-getmail/)
... but that blog post is from 2008, and my synaptic sees getmail4 in the repositories....

Or does anyone have good or bad experience with the software from
[http://www.gmail-backup.com/](http://www.gmail-backup.com/)

Thanks in advance!

---

### Post by ajgreeny on 2011-01-02
I don't specifically bacvk up my mail, other than that in ther mail folder of my ~/.thunderbird folder in home, which gets backed up with everything else.

However, the gmail server has a storage of 7GB for a standard gmail account; I don't know how many emails that would mean, but my 2000 or so emails is using just 2% of the space available.  If you don't delete mail from the server it just sits there, so that is my backup, if I need it.

---

### Post by bodhidharma on 2011-01-03
Well, my goal was to have my *personal* backup... sort of the FOSS way, don't trust the big guys, etc.  Also, slashdot had a story in the last 24 hours of yahoo loosing entire mail accounts of some users, and while I trust Google more than them, things could happen.  So I just want to get a copy of all my 40k mail messages (=42% of my available space, according to gmail) down onto my machine where I could back them up as I see fit (burn DVDs and bury them in the backyard, or something).

Thanks!

---

### Post by mastablasta on 2011-01-03
you oculd use an email client and make a backup file form the emails and then burn it.

---

### Post by Megaptera on 2011-01-03
I auto forward everything to a free Yahoo mail account. No intervention on my part after set up and it's all there just in case.

---

### Post by ba0bab on 2011-02-14
I use the program Gmail Backup [www.gmail-backup.com/](www.gmail-backup.com/), been using it for 2 years now. It's not updated since 2009, but it does the job.

I can't get the dependencies for the newest version to play nice on Ubuntu, though, so instead I installed it in my XP virtual machine and runs it from there every 14 days.

Edit: If you manage to install the newest version on Ubuntu, please share it here :)

---

### Post by Habitual on 2011-02-14
> **mastablasta said:**
> you oculd use an email client and make a backup file form the emails and then burn it.

FYI: Only true for POP access, not IMAP.

---

### Post by lisati on 2011-02-14
> **Megaptera said:**
> I auto forward everything to a free Yahoo mail account. No intervention on my part after set up and it's all there just in case.
I do the opposite: I forward mail from Yahoo and Gmail to my home server. Sometimes there's a problem when the server forwarding the message gets itself listed on a DNSBL server somewhere (this seems to happen for me more often with Yahoo than Gmail) and sometimes amavis does a whinge based on DKIM that the message has been altered, but this works well enough for me.

---

### Post by Baji on 2011-03-24
gmail backup.... the zip file only works for python 2.5, so no go on maverick, however, the svn version works...

```

sudo apt-get install python-wxgtk2.8
svn checkout http://gmail-backup-com.googlecode.com/svn/trunk/ gmail-backup/
cd gmail-backup
python2.6 gmail-backup-gui.py
```

works like a charm

---

### Post by ba0bab on 2011-03-24
Hey thx, but that's an old version, right? Older than the .exe file for windows? Because if that's true, I'd rather just use the exe version in a VM

---

### Post by deconstrained on 2011-03-24
Thunderbird.

---

### Post by helloise on 2011-11-11
> **Baji said:**
> gmail backup.... the zip file only works for python 2.5, so no go on maverick, however, the svn version works...

```

sudo apt-get install python-wxgtk2.8
svn checkout http://gmail-backup-com.googlecode.com/svn/trunk/ gmail-backup/
cd gmail-backup
python2.6 gmail-backup-gui.py
```

works like a charm

mine not working :(

---

