---
title: "rsync problems"
date: 2010-02-26
forum: General Help
---

### Post by switch10 on 2010-02-26
I used to use plain old cp to make backups, rsync looks like it can do exactly what I want.  I really like the fact that just the changed files get transfered.  I spent almost the whole day reading the man pages, and I thought I had all of the options that I wanted.  Here is what I am using.
```
 rsync -vrtlz --progress --stats --perms --exclude '*~' 'Music' /home/dave/ /home/dave/server/backup/desktop/dave 
```

I tried putting in the -e option but I get this error constantly with it, even though it still transfers the files.  Well, normally it does, it seems to be stuck on this last error for about 30 min;
```
 rsync: failed to set times on "/home/dave/server/media/Music/S/Steve Earle * Townes Van Zandt * Guy Clark/Together at the Bluebird Cafe": Invalid argument (22) 
```
so I took out the -e

I also tried putting in the --delete option, but it started deleting the files not transferring them!!  I was under the impression that the files that I deleted off the host would not be transfered to my server with this option.  

Another thing, am I using the --exclude option correctly?

The major issue I am having though, is that even when rsync finishes, it doesn't transfer all of my files.  It seems like it transfers all of them to a point, and then just stops.

does anyone know what I am doing wrong here?

Thanks a lot.

Dave

---

### Post by switch10 on 2010-02-27
someone in the #ubuntu IRC pointed out that I had a "*" in a filename :rolleyes: I cant believe I didn't catch that..

I also removed the -t flag to get rid of that time error.  preserving the modification times is not that important to me anyway.

does anyone have any other ideas??

---

### Post by switch10 on 2010-02-27
This command:
```
 rsync -vrlz --progress --stats --perms --exclude '*~' 'Music' /home/dave/ /home/dave/server/backup/desktop/dave 
```

copies all of the files in my /home directory, as well as the directories, but there is nothing in the directories!?!?  I have the recursive option on (-r).  

Whats going on?

---

### Post by jswoods7 on 2010-02-27
I think you need an extra '--exclude' in there:

rsync -vrlz --progress --stats --perms --exclude '*~' --exclude 'Music' /home/dave/ /home/dave/server/backup/desktop/dave

---

### Post by switch10 on 2010-02-27
> **jswoods7 said:**
> I think you need an extra '--exclude' in there:

rsync -vrlz --progress --stats --perms --exclude '*~' --exclude 'Music' /home/dave/ /home/dave/server/backup/desktop/dave

Thanks!! I will try that.

---

### Post by cong06 on 2010-02-27
Instead of all those options, there's a shortcut which makes alot of sense to me:

--archive, -a

I think it might be more then "you need" but It's probably worth it.

---

### Post by switch10 on 2010-02-27
Im an idiot...  I have my NAS mounted at ~/server and so rsync was backing up in a constant loop.  I set a new option to --exclude 'server'.  Hopefully that helps...

---

### Post by jamesisin on 2010-02-27
Yeah, I usually mount things under /media and not under my /home directory.  If you use Samba shares you'll want to exclude your Samba folder as well.  Take a look at this thread about backing up /home directories:

[http://ubuntuforums.org/showthread.php?t=1409050](http://ubuntuforums.org/showthread.php?t=1409050)

---

### Post by switch10 on 2010-02-27
> **jamesisin said:**
> Yeah, I usually mount things under /media and not under my /home directory.  If you use Samba shares you'll want to exclude your Samba folder as well.  Take a look at this thread about backing up /home directories:

[http://ubuntuforums.org/showthread.php?t=1409050](http://ubuntuforums.org/showthread.php?t=1409050)

Thanks.  Yeah I usually mount things under /media as well.  I'm just tring something new with this.  If it doesn't work out, I will put it back in /media.  I dont really mind excluding the directory, I run this backup as a cron job, so I only have to type it in once.  

Thanks for the tip on the Samba dir.  Fortunately I don't use Samba shares.

Any other Ideas anyone?

I think I have everything working.  I just did a test backup and everything went smooth.  I even put in the --delete option, and it seemed to work out good.  I wish I understood the delete option a little better so it didn't make me so nervous.

---

### Post by jamesisin on 2010-02-27
Take a look at the options I settled upon in that thread I linked above.  The -a option is for archiving (and includes options like -l and -r).

You can see a fuller description of both -a and --delete in the man page, of course.

In terms of best practices, I would mount in /media and create links where necessary.  Is there a reason you think this is not a good solution?

---

### Post by switch10 on 2010-02-27
> **jamesisin said:**
> Take a look at the options I settled upon in that thread I linked above.  The -a option is for archiving (and includes options like -l and -r).

You can see a fuller description of both -a and --delete in the man page, of course.

In terms of best practices, I would mount in /media and create links where necessary.  Is there a reason you think this is not a good solution?

To tell you the truth, I didn't anticipate any problems with mounting in the /home dir, and its easier to type in the terminal.  ~/server is easier than /media/server.  thats it really...  I may move it back to media.

I like what the -a option does, but I find it easier to type out the longer -- options, so I remember what they do exactly.  i.e. I can remember what --perms does better than -p, etc.  I am running rsync as a cron job, so the option short cuts while typing aren't as big of a deal as getting them right.

---

### Post by cjhabs on 2010-02-27
--delete is an option to keep the source and destination in sync - if the file was deleted on the source, it will be deleted from the destination.

---

### Post by switch10 on 2010-02-27
> **cjhabs said:**
> --delete is an option to keep the source and destination in sync - if the file was deleted on the source, it will be deleted from the destination.

thanks.  Yeah I figured out what my problem was with the --delete option.  I was backing up Music folders from 2 different machines to my NAS.  They each had different songs on them.  

I took out the --delete option in rsync for these directories, so hopefully it will just merge them.

---

### Post by jamesisin on 2010-02-27
If you create a link in ~/ called Server which then links to /media/Server that should be the same as far as use goes.

---

### Post by switch10 on 2010-02-27
> **jamesisin said:**
> If you create a link in ~/ called Server which then links to /media/Server that should be the same as far as use goes.

Hmm.  That is a great idea.. Thanks, I just did that and it works great.

---

### Post by jamesisin on 2010-02-28
I guess that's why they call them 'best practices'.  Excellent news.

Remember to mark your thread as SOLVED in Thread Tools above.

---

