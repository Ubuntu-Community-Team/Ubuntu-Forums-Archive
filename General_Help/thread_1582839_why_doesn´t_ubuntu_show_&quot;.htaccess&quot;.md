---
title: "why doesn´t ubuntu show &quot;.htaccess&quot;"
date: 2010-09-27
forum: General Help
---

### Post by Tom of Helatrobus on 2010-09-27
I´m having some issues with apache and found that some previously installed .htaccess files might be to blame. I know these files are there because when I type in the terminal :

sudo nano /var/www/filename/.htaccess

... the file pops up. but when I type: 

cd /var/www/filename
ls -l

... then there is no .htaccess file to be seen. Why is that? This isn´t limited to the terminal. I can´t see the .htaccess files ANYWHERE in ubuntu.

---

### Post by Tom of Helatrobus on 2010-09-27
Nevermind: 

to view hidden files in ubuntu: 
[URL="http://www.howtogeek.com/howto/ubuntu/view-hidden-files-and-folders-in-ubuntu-file-browser/"]
http://www.howtogeek.com/howto/ubuntu/view-hidden-files-and-folders-in-ubuntu-file-browser/ [/URL]

to view hidden files in terminal :

[http://ubuntuforums.org/showthread.php?t=625183](http://ubuntuforums.org/showthread.php?t=625183)

---

### Post by NikoC on 2010-09-27
And what if you type:
ls -Al

This will also show hidden files. Files with '.' in front of the filename are hidden.
Also when you open nautilus (filebrowser) you can type Ctrl+H which is the toggle for showing or not showing hidden files.

Cheerio

---

### Post by Tom of Helatrobus on 2010-09-27
> **NikoC said:**
> And what if you type:
ls -Al

This will also show hidden files. Files with '.' in front of the filename are hidden.
Also when you open nautilus (filebrowser) you can type Ctrl+H which is the toggle for showing or not showing hidden files.

Cheerio

Thanks, I´ll try that...

---

