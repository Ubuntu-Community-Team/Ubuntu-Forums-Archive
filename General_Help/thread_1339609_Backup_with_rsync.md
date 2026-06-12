---
title: "Backup with rsync"
date: 2009-11-27
forum: General Help
---

### Post by ubudog on 2009-11-27
How do I make a backup with rsync?

---

### Post by mdurham on 2009-11-27
> **ubudog said:**
> How do I make a backup with rsync?

What is it that you want to backup? Complete system? Home directory? Something else?

---

### Post by NFblaze on 2009-11-27
If you download PartedMagic 4.6 iso and burn it to a LiveCD it has rsync and a graphical frontend for it called Grsync. It's pretty simple to use from there.

Otherwise you can read the huge man page on rsync.

---

### Post by ubudog on 2009-11-28
> **mdurham said:**
> What is it that you want to backup? Complete system? Home directory? Something else?

Home directory.

---

### Post by ubudog on 2009-11-28
> **NFblaze said:**
> If you download PartedMagic 4.6 iso and burn it to a LiveCD it has rsync and a graphical frontend for it called Grsync. It's pretty simple to use from there.

Otherwise you can read the huge man page on rsync.

Thanks might read the man page.

---

### Post by mdurham on 2009-11-28
You could try using grsync, a graphical rsync front end, it's in the repos.

---

### Post by coffee on 2009-11-28
I have a python app I am working on that will help you get this done.  I am hosting it [[COLOR="Blue"]here[/COLOR]]("http://code.google.com/p/savethehouse/").

Download the file (*.tar.gz or *.zip up to you).

in the shell prompt:
```
#mkdir ~/bin
```

extract the downloaded file to the new dir.  Follow the README file and get the config.ini file setup per your needs and directory structure. You will need to modify line #8 in sth.py to reflect you home directory. Then you should be good to go.

coffee

---

### Post by XCan on 2009-11-28
> **ubudog said:**
> Home directory.

```
 rsync -avz --delete /home/ubudog /path/to/backup/dir 
``` That's it! The --delete flag can of course be omitted and will only ensure that files not existing in your home dir are also deleted from your backup dir.

---

### Post by ubudog on 2009-11-29
> **XCan said:**
> ```
 rsync -avz --delete /home/ubudog /path/to/backup/dir 
``` That's it! The --delete flag can of course be omitted and will only ensure that files not existing in your home dir are also deleted from your backup dir.

Thanks!  :p

---

### Post by ubudog on 2009-11-29
Just wrote a script to do it and backup in progress.  Is there a way to make this happen at a certain time each day?

---

### Post by XCan on 2009-11-29
Sure, you can use crontab to put it on schedule, I'm a little bit rusty, but the following should work:

1) Type "crontab -e" to edit your crontab
2) Add 37 13 * * * /path/to/your/script"
3) Save the file
4) (Optional) Check which crontabs you've enabled by "crontab -l"

In step 2, the entry means that you will run your script at 13:37 each day, you can specify it even further with days/weeks/months and so on. [http://www.crontabrocks.org/](http://www.crontabrocks.org/) is a quick and nice guide to crontab. :)

---

### Post by ubudog on 2009-11-29
> **XCan said:**
> Sure, you can use crontab to put it on schedule, I'm a little bit rusty, but the following should work:

1) Type "crontab -e" to edit your crontab
2) Add 37 13 * * * /path/to/your/script"
3) Save the file
4) (Optional) Check which crontabs you've enabled by "crontab -l"

In step 2, the entry means that you will run your script at 13:37 each day, you can specify it even further with days/weeks/months and so on. [http://www.crontabrocks.org/](http://www.crontabrocks.org/) is a quick and nice guide to crontab. :)

Thanks!

---

### Post by ubudog on 2009-11-29
Is it possible to make a window pop up after the backup has completed running that says something like "Backup Completed"?

---

### Post by NFblaze on 2009-11-29
> **ubudog said:**
> Is it possible to make a window pop up after the backup has completed running that says something like "Backup Completed"?

One method of producing a messagebox/ window on screen that I've used is to use the *xmessage* command. It's not a pretty-looking box tho, I'm sure someone else may have a more asthetically pleasing command.

---

### Post by ubudog on 2009-11-29
> **NFblaze said:**
> One method of producing a messagebox/ window on screen that I've used is to use the *xmessage* command. It's not a pretty-looking box tho, I'm sure someone else may have a more asthetically pleasing command.

Xmessage works.  Any other options?

---

### Post by NFblaze on 2009-11-29
Actually, yes upon a quick google search or xmessage I found this article which gives a quick tutorial on the Gnome messagebox tool Zenity and the KDE version.

[http://linux.byexamples.com/archives/87/using-gui-dialog-box/#comments]("http://linux.byexamples.com/archives/87/using-gui-dialog-box/#comments")

---

### Post by ubudog on 2009-11-29
> **NFblaze said:**
> Actually, yes upon a quick google search or xmessage I found this article which gives a quick tutorial on the Gnome messagebox tool Zenity and the KDE version.

[http://linux.byexamples.com/archives/87/using-gui-dialog-box/#comments]("http://linux.byexamples.com/archives/87/using-gui-dialog-box/#comments")

Nice! Thanks! :p

---

