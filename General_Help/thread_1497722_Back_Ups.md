---
title: "Back Ups"
date: 2010-05-30
forum: General Help
---

### Post by Jonny87 on 2010-05-30
I'm running 10:04 64bit, and I'm looking for an effective method/application to back up all user data and if possible installed applications so that in the event of accidental loss or re-install I can restore it back to the exact way it was at the time of back up.

Some key things I'm looking for is that the backup file/s take up as little space as possible, is easy as possible, and can be set do it on a regular bases automatically.

Does any one know of an application or a method that would best do this?

---

### Post by lovinglinux on 2010-05-31
I develop a Firefox extension that is good for the "installed applications" part. It doesn't backup the files from your directory, but generates a list of installed applications, that can be installed in batch mode later. It also allows you to save the packages in the cache and export a backup with packages included.

Take a look at [http://umarks-extension.blogspot.com](http://umarks-extension.blogspot.com)

---

### Post by sdennie on 2010-05-31
You may want to look at Simple Backup.  You can install it with:

```

sudo apt-get install sbackup

```

And then find it in System->Administration->Simple Backup

If that doesn't suit your needs, you'll probably want to look at rsync and/or rsnapshot.  There are various tutorials on the web about how to use them.

---

### Post by Jonny87 on 2010-05-31
> **sdennie said:**
> You may want to look at Simple Backup.  You can install it with:

```

sudo apt-get install sbackup

```And then find it in System->Administration->Simple Backup

If that doesn't suit your needs, you'll probably want to look at rsync and/or rsnapshot.  There are various tutorials on the web about how to use them.

Probably should have mentioned that I currently have Simple Backup but haven't been able to get it to work. I'll continue to have a bit of a play around with it but I'll keep in mind the rsync and rsnapshot. 

Just in case if anyone knows of any other application that is good let me know. I'll continue to play with simple backup and let you know if I work out why it wasn't working.

---

### Post by Jonny87 on 2010-06-01
I've tried Simple backup again. still doing the same. it says that its started and tells me that the process id but if i look in the system monitor it's labeled as Zombie. Usually the simple backup will also freeze and I have to kill the process to actually close the thing.

Any Ideas as to why its not working?

---

### Post by inameiname on 2010-06-01
Install Remastersys (you'll need the Remastersys repo first to  download). It's the easiest way for me to do what you want.

And then open it, and hit "Backup", and it'll make an ISO just like that  with absolutely everything that you have on your computer, including  whatever "My Documents" you have too. 

You can then just insert the custom live cd/dvd, made with the ISO file,  and install it on any computer, just like the original live cd ISO that  you used, and will be exactly as it was when you made the backup.

---

### Post by Jonny87 on 2010-06-01
Thanks, will keep that in mind, sounds handy.

---

