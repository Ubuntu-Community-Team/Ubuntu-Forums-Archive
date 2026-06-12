---
title: "Web development, git, and file permissions"
date: 2009-06-30
forum: General Help
---

### Post by Belerophon on 2009-06-30
Hi.

I am posting to see what's the common approach in my situation:

- I am doing web development wit git behind it, and in my pc I have Apache configured with userdir mod. My local repo is in my public html. I got the site up and running after setting less restrictive permissions to the repo.

The thing is that if when I pull something remotely that did not exist in my local repo, the new files and folders are created with default permissions, and cannot be read by Apache. The same when I am the one creating new files and commiting.

So, for each new file that appears in my repo, I need to go and change the permissions. This is a little annoying....

What do you guys do to avoid this?

Thank you.

---

### Post by unutbu on 2009-06-30
There is a package called incron which you can configure to monitor a directory. 
You can create a rule such that whenever a new file is created in that directory, a command or script is executed. That command, for example, could run
```

chmod -R 755 /var/www
chown -R www:www /var/www
```

(There are ways to tailor the command to the specific file created, so you don't have to use the -R flag too...)

The only problem that may affect you is that incron monitors fixed directories and does not expand its monitoring dynamically to include subdirectories. So if git creates a subdirectory, I'm not too confident that incron will execute the script when files are created in the subdirectory.

A possible solution if this turns out to be a problem is to use dirmon (see [http://ubuntuforums.org/showthread.php?t=1104716](http://ubuntuforums.org/showthread.php?t=1104716)). It does monitor directories "recursively".
The advantage of incron is that it comes from the official repos. dirmon is just a rink-a-dink script that I wrote. 

PS. If you do "apt-cache search inotify" you will find a alternative ways to directory monitoring. (gamin, inoticoming, inotify-tools, iwatch. I don't have any experience with these, however.)

---

### Post by unutbu on 2009-06-30
Here is an example of how to setup incron:
[http://ubuntuforums.org/showpost.php?p=7379763&postcount=3](http://ubuntuforums.org/showpost.php?p=7379763&postcount=3)

---

### Post by Belerophon on 2009-07-01
If incron can't monitor subdirectories, than it's not really what I'm am looking for...:/

I was now thinking of trying a post-update git hook...but I think it will need root privileges ...right ? :S

---

