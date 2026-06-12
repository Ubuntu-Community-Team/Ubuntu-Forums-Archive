---
title: "Thunderbird under multiple OSs"
date: 2006-06-21
forum: General Help
---

### Post by pvent on 2006-06-21
I have used Thunderbird under Windows XP before I installed Linux. Now I Installed Thunderbird under Linux, but I want both Thunderbirds (the one under Windows and the one under Linux) to use the same database. More specifically, I want the Linux one to use the database and folders that the Windows one has been using. Is there a way to do this?

---

### Post by wylfing on 2006-06-21
Yes and no.

Here is a way to do it (assuming locally-stored POP): put your mailboxes in a location that is *writable* from both OSs and then instruct Thunderbird to look at that location for mail. IIRC you need to look under your account settings and there is a field where you can specify the location of the mailbox file.

Note that I said writable, not visible. If you have your current mailbox files on an NTFS partition, you cannot write to that from Linux (not safely anyway). You'll need to move them to, say, a FAT32 partition so that both Linux and Windows can write new mail into the mailbox files.

The "no" part of my initial answer is that under this setup you will see some screwy behavior, such as a high level of reindexing. This is not so bad as long as you keep your mailboxes cleaned up and archive things promptly. If you're lazy like me it's a major pain, though.

---

### Post by bollix47 on 2006-06-21
I used the info [here]("http://3dgpu.com/forums/index.php?showtopic=4953&pid=55355&st=0&#entry55355") but my windows was **_not_** NTFS.

---

### Post by Legion on 2006-06-21
[QUOTE=pvent]I have used Thunderbird under Windows XP before I installed Linux. Now I Installed Thunderbird under Linux, but I want both Thunderbirds (the one under Windows and the one under Linux) to use the same database. More specifically, I want the Linux one to use the database and folders that the Windows one has been using. Is there a way to do this?[/QUOTE]

It sounds like what you REALLY want is an IMAP email account.

Your email provider may allow you to access your account via IMAP instead of POP, you'd have to check.

---

### Post by blackpaw on 2006-06-26
well, I don't want to test this but assuming you are using a FAT partition for windows and have it mounted writeable at startup of Ubuntu you should be able to point Thunderbird to the mailbox file there...

Now, the directory with all settings of a profile is stored in Windows under 
*Documents and Settings\ username\Application Data\Thunderbird\Profiles\XXXXXXXX.default*

Under Linux the same directory is stored in *~/.mozilla-thunderbird/YYYYYYYY.default*

the settings are stored in a file called "profiles.ini"
There it says "Path=XXXXXXXX.default"

can't you just create a symlink to the directory on the windows partition here, call it - say - ZZZZZZZZ.default and then point the profiles.ini to that directory?

I might try that myself....

*is pretty curious*


andreas

---

