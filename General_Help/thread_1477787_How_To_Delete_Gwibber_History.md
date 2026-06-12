---
title: "How To Delete Gwibber History?"
date: 2010-05-09
forum: General Help
---

### Post by AJH101 on 2010-05-09
Upgrading to Lucid I tried out the memenu and realised I had been signed up to Twitter for years receiving tweets (although not forwaded to my phone) that I do not want to receive. Is it possible to stop this long list of tweets from showing in Gwibber now they are there?

---

### Post by WorMzy on 2010-05-09
If it's storing anything locally, it'll be in your home folder. Open nautilus and browse to your home folder, then show hidden files by pressing Ctrl+H, and look for a file or folder called ".gwibber".

---

### Post by AJH101 on 2010-05-09
Thanks but that was the first thing I did! And there is no such file/folder! Has anyone else got any ideas please?

---

### Post by YuiDaoren on 2010-05-17
Sorry, never mind, my info was wrong.

---

### Post by depp on 2010-06-01
.local/share/desktop-couch
.config/desktop-couch
.cache/desktop-couch
I delete all of them.

---

### Post by Sylvain Falardeau on 2010-07-09
To see the messages cached by Gwibber, use your browser to connect to desktop-couch:

file:///home/<your_username>/.local/share/desktop-couch/couchdb.html

This page will show you a link to login on your desktop-couch instance.

You will see Couch databases (tables) and one is "gwibber_messages". The number of documents is the number of messages cached by Gwibber.

After a while you may have a lot of messages in there and from time to time, your machine is taking 100% CPU for the beam.smp (desktop-couch) process.

You can delete the table "gwibber_messages" by clicking it and clicking "Delete database...". Then you logout/login and the database will be recreated by gwibber-service (you can also kill and restart gwibber-services manually to replace logout/login).

---

### Post by Sylvain Falardeau on 2010-07-28
I have made a small Python script to delete all Gwibber history more than 5 days old. It connects to your desktop-couch, delete the messages and compact the database after.

Warning: I do not have tested it with Ubuntu One and I don't know all the side effects of deleting data from your local desktop-couch.

You can connect with Futon (use your browser on file:///home/youruser/.local/share/desktop-couch/couchdb.html) and go to the Tools/Status menu. You will see the progression of views/compaction.

Script gwibber-delete-history
```

#!/usr/bin/python

# Made by Sylvain Falardeau <sylvainf@xsoli.com>
# This script is in the public domain

# On Ubuntu 10.04, you need python-desktopcouch package
# Edit the KEEP_LAST_DAYS constant to the number of days you want to keep

import sys
import time
from desktopcouch.records.server import CouchDatabase

KEEP_LAST_DAYS = 5

DELETE_HISTORY_JS = """function(doc) {
    if (doc.record_type == 'http://gwibber.com/couch/message') {
         emit(doc.time, doc)
    }
}"""
SECONDS_PER_DAY = 86400


gwibber_messages = CouchDatabase("gwibber_messages", create=False)
if not gwibber_messages.view_exists("delete_history"):
    print "Creating view delete_history (may take a while to index)"
    gwibber_messages.add_view("delete_history", DELETE_HISTORY_JS, None)

delete_up_to = int(time.time() - KEEP_LAST_DAYS * SECONDS_PER_DAY)
messages = gwibber_messages.execute_view("delete_history")

print "Deleting messages older than %d days in gwibber_messages" % KEEP_LAST_DAYS
count = 0
for msg in messages[0:delete_up_to]:
    if count % 1000 == 0:
        sys.stdout.write(".")
    gwibber_messages.db.delete(msg.value)
    count += 1

print
print
print "Start compacting database gwibber_messages (see Futon Status for details)"
gwibber_messages.db.compact()

```

---

### Post by AJH101 on 2010-07-29
Sylvain this sounds fantastic than you but I am afraid I need some instructions that assume no prior knowledge of coding etc! Thank you...

---

### Post by Sylvain Falardeau on 2010-07-29
Oh, sorry!


[LIST=1]
[*]Open an editor (gedit) and copy/paste the content of the Python script.
[*]Save the file as "gwibber-delete-history".
[*]With Nautilus File Browser, right click on the file and choose "Properties".
[*]In the "Permissions" tab, check the "Allow executing file as program" and Close the window.
[*]You can then double click on the file. You will select "Run in terminal". In the terminal window, you will see progression messages. IT CAN TAKE A WHILE (more than hours if you database is currently big).
[*]In your web browser, choose File/Open File and get to .local/share/desktop-couch/couchdb.html (the files beginning by dots may not be shown but you can type in the Location: field). You will login in Futon, the CouchDB web interface where the data is stored.
[*]In the menu on the right, choose "Status" and follow the progression.
[*]You can also select "Overview" to see the number of documents and the size of the "gwibber_messages" database.
[*]When the deletion is done for the first time, the database will grow a lot before the compaction occurs and make is small again.
[/LIST]
I hope this helps.

---

### Post by abumaia on 2011-01-15
> **Sylvain Falardeau said:**
> To see the messages cached by Gwibber, use your browser to connect to desktop-couch:

file:///home/<your_username>/.local/share/desktop-couch/couchdb.html

This page will show you a link to login on your desktop-couch instance.

You will see Couch databases (tables) and one is "gwibber_messages". The number of documents is the number of messages cached by Gwibber.

After a while you may have a lot of messages in there and from time to time, your machine is taking 100% CPU for the beam.smp (desktop-couch) process.

You can delete the table "gwibber_messages" by clicking it and clicking "Delete database...". Then you logout/login and the database will be recreated by gwibber-service (you can also kill and restart gwibber-services manually to replace logout/login).

What do you do if you open couchdb.html and click the link, then get an error screen saying it cannot connect to server localhost:#####?

---

### Post by Sylvain Falardeau on 2011-01-17
At the shell, type:

```

$ pgrep -l couch


```

You should see process ID (numbers) and some couch process names:

```

3943 desktopcouch-se
4059 couchdb
4087 couchdb
4104 desktopcouch-se

```

If you don't see that, it means you don't have the desktop-couch service running. This service should be started automatically when you start your session. I don't know why it is not running (if this is the case).

---

### Post by abumaia on 2011-01-23
correct, I have the two couchdb's, but the two desktopcouch-se's are not shown. Now to figure out why, and how to fix it.

---

### Post by Sylvain Falardeau on 2011-01-23
I am not sure how to help you.

Your service seems to be running but maybe it's the port number in the html file that is wrong? I am not an expert on Couchdb so I don't know the exact behavior in this case.

---

### Post by ronix on 2011-05-20
> **Sylvain Falardeau said:**
> I have made a small Python script...

Cool! Worked perfectly for me.

Best regards,
Max.

---

### Post by brashley46 on 2011-11-05
Sylvain's Python script does not work in Xubuntu 11.10; I don't know where the Gwibber database is but it does not seem to be in couchdb any more.

---

### Post by gotgenes on 2012-04-11
Gwibber now uses SQLite as its backend storage by default, unless CouchDB is already installed. (CouchDB is not installed on a default Ubuntu installation). Remove your Gwibber history with

```

rm -r ~/.config/gwibber/
rm -r ~/.cache/gwibber/
```

---

