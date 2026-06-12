---
title: "Email expiry, self-deleting emails..."
date: 2012-02-13
forum: General Help
---

### Post by quickk on 2012-02-13
Hi everyone, 

   I've been thinking a lot about what the best way to manage my email might be.   In the past, I had a bunch of folders and I would try to diligently file all messages away in the right places.  Eventually though, I found this to be very difficult to manage since I ended up with too many folders, and searching through all these different folders was quite tedious.   Now I try to keep everything in the inbox and use thunderbird's quick filter to find what I want.  

   The problem is that I still get way too much email.   There are currently over 3000 messages in my inbox, and I fear that this number will soon become unmanageable.    The vast majority of the messages are not anything that I want to keep, but for some reason I am not diligent enough to delete them right away.  

   Is there a way to have my email client (thunderbird, or any other client) by default automatically delete email that is older than, say, 1 month?   That is, unless I actively specify that I want to keep a message, it would be nice if it just was deleted.   I don't really need to keep that message from 1 year ago that just says "sounds good", or "meeting at noon."

   Has anyone else thought about this?   A quick search through the Thunderbird extensions reveal nothing...

---

### Post by SeijiSensei on 2012-02-13
If you have scripting skills and knowledge of a language with IMAP functions, you can write a script that runs each night and uses IMAP commands to move messages older than a cutoff date to an archive folder.

A much easier solution is to use the built-in "logrotate" application.  You can set up a logrotate configuration that will archive your inbox each day, week, or month.  Create a logrotate script for your inbox (I call it "mailbackup" below) like this:

```

/var/spool/mail/yourusername { 
    monthly
    rotate 13
    postrotate
        cp -f /var/spool/mail/yourusername.* /home/yourusername/mail
    endscript
}

```

then copy the file into /etc/logrotate.d/ using sudo (e.g., "sudo cp /path/to/mailbackup /etc/logrotate.d").  Now your inbox will be renamed to yourusername.1 on the first of each month, and all prior backups will be renumbered accordingly.  A rotate value of 13 will keep 13 months of backups; adjust as needed.  All these backups will be stored in /var/spool/mail; make sure you have enough space there.  The "postrotate" command copies all the backups into /home/username/mail which is the usual location for mail folders.  If you use a different location, adjust accordingly.

For more help read the logrotate "manual" page by typing "man logrotate" at a terminal prompt.

If you use IMAP, you might find you'll need to "subscribe" to the backups when they are first created.

---

### Post by HiImTye on 2012-02-13
in thunderbird, right click on the folder (if you are using unified inbox, you will need to click the > arrow and then right click the correct inbox) then choose the retention tab. from here you can choose a maximum age to keep them. if you want to keep messages for longer you can move them into a different folder and keep your retention policy normal in that folder

---

### Post by quickk on 2012-02-14
Thank you to both of you for some interesting suggestions.   I think that I'll give SeijiSensei's suggestion a go for now.   It pretty much does what I want and so I just have to remember to move important messages!

Thanks!

---

