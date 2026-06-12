---
title: "tar and crontab...."
date: 2010-04-06
forum: General Help
---

### Post by AoSteve on 2010-04-06
Ok, here's my deal...   I'm trying to get the following output and find out what and how I can do what I'm trying to do.   This must be done with a script so I cannot do anything with the GUI.

I want to tar an entire directory, something like an MS-Dos entry would be :

tar /mydirectory/*.* 

However, if there's anyway; I'd like to be able to do something like this.

Keep a week worth of backups; every backup would be named something like TueApr5.tgz  I'm not even sure it's possible to name the file using grep or not.  I'm nowhere near skilled enough to get it right if so.   I've tried.. plenty of times.   

Last but not least; I'd like to echo the output to a file..   How could I go about doing this and then have it setup in crontab to run on shutdown?   I'm simply wanting to save all my schoolwork progress in a folder on my disk each time it shuts down.  I've lost too many assignments in three years and using Windows; these backups were simple to setup.   I'm not so good with Linux yet lol.   Maybe someone can shed some light for me.

One last thing I almost forgot.   How can I manually set a script up to run on shutdown through crontab?   I'm not exactly sure how crontab works personally; but I'm more then willing to learn.

---

### Post by falconindy on 2010-04-06
You should use the following invocation for tar:

```
tar -czf "$(date +%a%b%d)bkup.tar.gz" /path/to/dir
```

Throw this into a script file and execute it from cron:

```
@reboot   /path/to/script
```

...though I'm not familiar with Vixie cron (can someone confirm Ubuntu still uses Vixie?) and this may actually be run at startup, not shutdown.

Feel free to change the date format as you'd like -- `man date` will give you a list of tokens. I would personally use something such as +%Y-%m-%d as the list is more naturally sorted.

---

### Post by AoSteve on 2010-04-06
Ok, now I imagine I'll have to add a timestamp as well seeing as if I shutdown twice in a day; it'd backup with the same filename.  But I see how it works.  I guess I was using the wrong options.  I'm not extremely good with linux commands yet.  The -czf are all one option or are they a set of grouped options?  Sorry for the lack of intelligence, but I'm learning more and more on the command line every day.

I'm not sure about the crontab deal still.   Is there any way to manually add my script through a configuration file?

---

### Post by AoSteve on 2010-04-06
Another question I wasn't sure about.  When making this script run during shutdown; how can I have it have root permissions so I can save to.. anywhere on the disk I wish to save the files at?   I'd prefer to save the files in a folder that I can access with only my account and preferably; not in my home directory as it's on a separate disk?

---

### Post by falconindy on 2010-04-06
> **AoSteve said:**
> Ok, now I imagine I'll have to add a timestamp as well seeing as if I shutdown twice in a day; it'd backup with the same filename.  But I see how it works.  I guess I was using the wrong options.  I'm not extremely good with linux commands yet.  The -czf are all one option or are they a set of grouped options?  Sorry for the lack of intelligence, but I'm learning more and more on the command line every day.

I'm not sure about the crontab deal still.   Is there any way to manually add my script through a configuration file?

-czf are 3 separate options crammed together.

-c create an archive
-z compress it with gzip
-f use this filename (this is really an extension of -c)

If you'd like a GUI for cron, i recommend gnome-schedule. If you're feeling brave, just use 'crontab -e' from the terminal and enter the line i provided.

If you want the script to have root privileges, add it to root's crontab instead of yours (using `gksu gnome-schedule` or `sudo crontab -e`).

---

### Post by AoSteve on 2010-04-07
Excellent.   I'll have to tinker around with crontab a bit.  No way to learn better then by experience I always say.  I'll give it a shot!  Thanks falconindy!

---

