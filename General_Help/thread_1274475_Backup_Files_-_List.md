---
title: "Backup Files - List"
date: 2009-09-24
forum: General Help
---

### Post by Groover20 on 2009-09-24
I recently setup an old computer as an Ubuntu file server.  It mainly holds music, movies, pictures and personal files.

In order to be safe, I downloaded sbackup, and configured it so the pictures and personal files are backed up on a regular basis to another drive called backup.

Now, I would like to back up the list of files in my movie and music folders.  I do not want the actual files, simply their names.  I did a bit of research, but didn't find anything that seemed simple enough for me to do.

I hope someone here can help me.

Thanks in advance,

Groover20

---

### Post by nikhilbhardwaj on 2009-09-24
ls
lists file names
ls > newfile

---

### Post by Groover20 on 2009-09-24
Is it possbible to make this automatic, so let's say every Saturday night it does it?

---

### Post by nikhilbhardwaj on 2009-09-24
yup
you can use cron

---

### Post by Groover20 on 2009-09-24
Perfect...I didn't really know about Cron, but it looks like it could be VERY useful, especially on a server.

I got another question though.  How do I get the list to include what's in each folder, and each sub-folders^  Is it at all possible, or do I have to run separate jobs^

---

### Post by Groover20 on 2009-09-25
Ok, I found somewhat the option I wanted: ls */

Now, I tried to do the following in the terminal:
ls */ /media/Movies > backupmovielsit 

but it doesn't work.  is there a way to make it happen?

---

### Post by NoaHall on 2009-09-25
Which bit doesn't work? Try using two ">>"

---

### Post by Groover20 on 2009-09-25
With >> it gives me the listing of /media/Movies but not the content of any sub-folders.

Also tried in the terminal to do this in one operation:  cd /media/Movies ls */ > 
/home/server/backpmovielist

I guess that to achieve that I would have to write a script.

---

### Post by NoaHall on 2009-09-25
What EXACTLY are you putting into the command? 
Show your gaps, speech marks, etc.

Using 
```
  ls */ /home/noah >> nefile 
```

Works fine for me.

---

### Post by KyleRaynor on 2009-09-25
try this script, just place it in your $HOMEDIR/bin directory and have cron run it once a night. A quick google search should find hundreds of cron how-to's. 

```

#!/bin/bash
$musicDir=/your/music/dir/here
ls -R */ $musicDir >> $HOMEDIR/musiclist
exit 0

```

---

### Post by Groover20 on 2009-09-25
Noah, I didn't expressed myself clearly enough.  I meant that I was getting an output, but not the one I was hoping for.  It lists the files in my Movies folder, but not in the subfolders.

Here's exactly what I typed:
ls */ /media/multimedia/Movies >> backupmovielist

I'll try the script suggested by KyleRaynor and see how it works out.

---

### Post by NoaHall on 2009-09-25
Ah, I see.
ls -R would be what you're looking for, I think.

---

### Post by Groover20 on 2009-09-25
It worked!!

Thanks so much!

I'll still try the script, just so to get my feet wet with scripting.

Now, I have to wait until Monday morning to see if it worked as planned through CRON.

---

### Post by Groover20 on 2009-09-27
I just checked, and the CRON jobs ran as expected.  Thanks all for your help!

---

