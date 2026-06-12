---
title: "backup tool didn't backup anything!?"
date: 2012-06-24
forum: General Help
---

### Post by AlexBooton on 2012-06-24
Hi,

I ran the backup tool (system settings/backup) to backup the entire system to an external usb drive.

It ran for almost 24 hours and the progress window kept showing the files being backed up.  

BUT at the end of the process; there was no file created on the external drive (or anywhere else AFAICS).

Does this tool actually work?

Here were my settings:
[INDENT]Backup location /bu on <external drive>
Folders to back up: /
Folders to ignore: Trash,/proc,/lost+found,/mnt,/sys,/media,/dev
[/INDENT]

What did I do wrong?

If the backup was placed somewhere other than the external drive, is there an easy way to find it?  Possibly by listing all .tar files sorted by file size, descending?

Thanks,

AB

---

### Post by AlexBooton on 2012-06-24
Well I found the backup.

It's in /bu

I wanted it to go to the external drive.  But it didn't.  Why?

Also, when I tried to run a restore from the backup tool it took a while searching and then said "Operation Failed/Operation not supported".

I assume that's because it's looking where I told it to put the bu; but the bu isn't there!

I tried to restore from /bu (where the bu is) and it works.

But I don't want to fill up the main drive with backup.  How do I direct it to the external drive?

Thanks,

AB

---

### Post by AlexBooton on 2012-06-24
Well I think I just discovered the worst thing about the backup tool.  There is no option to select the files to be restored.  It's all or nothing.

That make it essentially worthless.

AB

---

### Post by Ms. Daisy on 2012-06-24
I recommend that you check this out:

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

There are tons of options for backing up your data and [Deja Dup]("http://techie-buzz.com/foss/deja-dup-ubuntu-1.html") is only one of them.  I guess it's installed by default because the developers feel it's the easiest to use.  I like [rsync]("https://help.ubuntu.com/community/rsync") myself.

---

### Post by mwinthrop on 2012-06-24
I use a luckybackup from the Ubuntu Software Center.  It works pretty well, though it does not do anything special as far as compression or anything.

---

### Post by AlexBooton on 2012-06-24
Thanks for all your replies.

I'm now playing with luckybackup as suggested by mwinthrop.

I like it b/c it uses rsync which Ms. Daisy suggested.

Thank you both.

One thing I notice is there doesn't seem to be any compression of the back up.  Is there a way to get compression?

Thanks,

AB

---

### Post by AlexBooton on 2012-06-24
Well I played a bit w/luckybackup and to a lesser extent with rsync.

AFAICS, there isn't any way to compress the bu with these tools.

I tried the rsync -z (and also --compress in a second trial) option and neither produces compressed backups.

Am I missing something?

Thanks,

AB

---

### Post by Ms. Daisy on 2012-06-24
I haven't tried lucky backup so I don't know its options.  Rsync has a huge number of options and honestly I haven't mastered them all. I think the compress -z option compresses the traffic so that the transfer of data takes less bandwidth as opposed to actually compressing the data (but I could be wrong, like I said I haven't mastered it).

Look at [tar]("https://help.ubuntu.com/community/BackupYourSystem/TAR") to compress your data.

---

### Post by AlexBooton on 2012-06-24
> **Ms. Daisy said:**
> I think the compress -z option compresses the traffic so that the transfer of data takes less bandwidth as opposed to actually compressing the data (but I could be wrong, like I said I haven't mastered it).

Look at [tar]("https://help.ubuntu.com/community/BackupYourSystem/TAR") to compress your data.

That's my understanding too -- that the -z option does what you said.

AFAICS, lucky is essentially a front end gui for rsync.  It generates and runs rsync commands.

Thanks for that link.  I'm actually testing one of the examples:
[INDENT]tar -cvpz <put options here> / | split -d -b 3900m - /name/of/backup.tar.gz.[/INDENT]

I use the fork to split simply because I'm backing up the entire system and generating one huge tarball doesn't feel optimal.

BUT there appears to be a problem.  I'm not sure about this but using split may preclude updating the tarball with newer/changed files.

AB

---

