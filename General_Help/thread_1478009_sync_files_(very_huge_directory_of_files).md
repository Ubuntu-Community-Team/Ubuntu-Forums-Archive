---
title: "sync files (very huge directory of files)"
date: 2010-05-09
forum: General Help
---

### Post by ClarkePeters on 2010-05-09
ubuntu hardy heron

I have amassed a great quantity of files, nearly 50,000 files (49,585 @ 9.6 gb).  I have to carry these files with me to my office, as we can't trust the internet connection we have, so I can't keep my files on a web server. So I have a usb hard drive that I keep a copy of my Documents folder on.  

My issue though, is that after I update my computer with new or edited files, I need to update the usb drive. My question then, concerns both stratagy and available software for keeping track. Of course, I could just keep up with what files I've edited, downloaded, or created, but I have a lot of interruptions in my job, and although my job is about 40% related to keeping up with all this content (editor, corpus manager, writer, curricula designer), about 60% of my job takes me away from my computer, so I just often can't keep up with my changes have been taking place. 

I tried unison, but when I finished, I had to indivually approve all 50,000 files for the first sync--I quit after about 5,000.  I was going to use GIT, the distrbutied version control history, but it has the same problem that when I initiallize, I have to wait forever and it bogs down my system so I can't work on other stuff, well, not efficiently. 

I'm thinking maybe I can't really efficiently sync that many files, so I'm also thinking of a new strategy, which is this, now that I have identical copies of my Documents folders. Maybe I'll just create a new folder, like, Working directory, or something, and GIT it, and only track newer changes. The only problem with this is that means I'll be pulling my files in and out of their own folders and into the working directory folder and then back to the appropriate categorized folders that they came from or need to be added too, and I'll have to do this twice, once on my system hard drive, and once on my usb hard drive. 

Any one with experience who can give me a better approach or strategy (software suggestions), I'd appreciate it.

---

### Post by SPr on 2010-05-09
[DropBox](www.dropbox.com)?

---

### Post by ClarkePeters on 2010-05-09
Dropbox seems really cool, but there isn't a lot of info. Looks like it  syncs across the web. As I said, at my office I can't trust the web, our servers get overloaded and it can take 20 minutes to download a single document, or worse, it will just go down altogether for a spell.

anyone else?

---

### Post by John Bean on 2010-05-09
If you have a USB disk that you can leave all the files on I would use rsync (or the graphical grsync) on both home and office computers to sync to the USB drive. Simple, reliable, effective, quick after the first full sync.

---

### Post by ClarkePeters on 2010-05-09
I sure wish I could trust my internet connection cause dropbox looks really cool.

here is a youtube demo:
[URL="http://www.youtube.com/watch?v=maQrWC-raFQ"]dropbox demo
[/URL]

It seems that you only have to install it on your own computers and not on a server, you just link your desired folders to email addresses and you can sync  your own files or share files instantly with others that have dropbox installed. if it works, it's an ingenius idea and wonder why no-one ever thought of this before. 

at anyrate, I may use it to solve my other problems, but for the problem of this post, I still can't trust my internet connection, so I'm still brainstorming.

---

### Post by SPr on 2010-05-09
I really do not want to sit through that terrible video again so I can't be certain but I do believe that it will sync to USB drives.

I agree the information on that website is minimal at best but I have heard good reports about dropbox.

---

### Post by ClarkePeters on 2010-05-09
thanks john bean, 
I thought about rsync. I don't have a problem working through the first sync, but can you tell me, will I have to physically answer "yes" to allow syncing of each of the files? (this is what happened with unison). That would take me like hours to sync 50,000 files.

---

### Post by John Bean on 2010-05-09
> **ClarkePeters said:**
> thanks john bean, 
I thought about rsync. I don't have a problem working through the first sync, but can you tell me, will I have to physically answer "yes" to allow syncing of each of the files? (this is what happened with unison). That would take me like hours to sync 50,000 files.

Install grsync and have a play. Setup is dead simple with all the common options available on a tabbed interface, operation is a button click away. No questions :-)

---

### Post by geoffm on 2010-05-09
It might not be optimal but here's a workaround I've been using:

use the copy command with the -ur option (update older files and recurse subdirectories), copy USB flash drive content to Local folder and copy local folder to USB drive

exemple:
```

cp -ru /media/GEOFFUSB/Documents/ ~/
cp -ru ~/Documents/ /media/GEOFFUSB/

```

you might find these options useful:
-L option if you want to copy symlink directories from the source as directories in the destination
-i option if you want cp to ask confirmation before overwriting

---

### Post by ClarkePeters on 2010-05-09
I don't know about only a work around because that actually seems pretty simple and useful. I never realized you could copy only updated files (-u), so cool. I think I'll give it a go.

thanks geoffm.

---

### Post by geoffm on 2010-05-09
> **ClarkePeters said:**
> I don't know about only a work around because that actually seems pretty simple and useful. I never realized you could copy only updated files (-u), so cool. I think I'll give it a go.

thanks geoffm.

Careful, though. I just realized that when it "updates" a file, it sets the destination file's  date as the current date instead of source file date. So if you're syncing more than 3 folders it might f*** you over.

---

### Post by dtfinch on 2010-05-09
rsync has a --backup option to preserve old revisions. By default it'll rename them. You can use --backup-dir to move old revisions to a different folder instead, and --delete to move deleted files the same as old revisions. You also want to add --times so that rsync will copy modification dates and use them to determine what needs to be updated, otherwise it compares every file. And if the source and destination are different filesystems (like fat32 on the usb), you'll want to use --modify-window to specify how many seconds tolerance to use when comparing times, because different filesystems round them differently.

We use rsync to back up our all file servers, millions of files, keeping past revisions. Though I'm not at work so I don't have the exact options we use.

[http://www.samba.org/ftp/rsync/rsync.html](http://www.samba.org/ftp/rsync/rsync.html)

---

### Post by ClarkePeters on 2010-05-11
dtfinch,
thanks so much for the rsync suggestion.

I tried out rsync with grsync gui and it worked perfectly. What amazed me was the speed at which it operated even on the first initial sync. It went through the 73,000 files (36,500 in each directory) in only 40 seconds (that was according to rsync's computer timer, but it sure felt like only 25 seconds). On the second run, after the initial sync, it took only 6 seconds. (for anyone reviewing this, keep in mind that I was syncing to a nearly identical folder as the source not to an empty one).

This was cool because I could run the simulation first to see how it would work before actually executing. (it was also a way to "try out" the program before committing)

Also, thanks for the other tips because I think I'll be using the --backup option for my programming code, which I've yet to sync. Don't know if I can do that in the gui but I can drop back to the terminal easily. (there's a "make backups" in the advance options in the gui but I haven't checked if that's the same as the --backup option from the command line, though I suspect it is).

Thanks again and thanks a heep!

edited: changed 100,000 to 73,000  (I had forgotten that I did a major clean up and also used fslint to eliminate hords of duplicate files before I tested rsync - grsync)

---

### Post by ClarkePeters on 2010-05-11
Oh, and John Bean, I forgot to thank you too for getting me in that direction (rsync/grsync).  When dtfinch said they were using it for millions of files, that's what gave me the extra shove to give it a try.
Thanks to you both.

---

