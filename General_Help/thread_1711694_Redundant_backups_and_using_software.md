---
title: "Redundant backups and using software"
date: 2011-03-21
forum: General Help
---

### Post by nslegacy163 on 2011-03-21
So here's my paranoid plan of back up:

 I have two 500GB externals and a 200GB internal HDDs for my desktop. One of the 500s is solely for backups of my desktop, netbook, and laptop. The other 500 is pretty much my "everything" drive. Literally everything (music, movies/videos, pictures, documents, etc) get saved to this external so I can access it on all my machines. The internal 200GB on my desktop is pretty much only used for temporary downloads, the OS (obviously) and things like that. Here's what I'd like to do: 

 I used deja dup to create a back up of my /home and my "everything" 500 onto the "back ups only" 500 but once I let my paranoia simmer for a second I thought, "what if my back up HDD fails?!" So I want to have two redundant backups on separate drives. First I figured I'd just chuck it on the other "everything" 500 but then I thought that since I'm using barely any room on the internal 200, I could just store a backup there. So that's my plan. My problem is that deja dup only really allows one location to run the scheduled backups. I saw this post:
 
 [http://ubuntuforums.org/showthread.php?t=35087&referrerid=1246731](http://ubuntuforums.org/showthread.php?t=35087&referrerid=1246731) 

 and think I could just do that for the redundant backup? Or is there a program I can get from the software center that allows me to schedule more than one backup on different locations? I looked into Back in Time but that's just a snapshot(?) and I didn't see a way to do what I liked...I think. 

 Any suggestions or help is great! Thanks everyone in advance, I love this community!

---

### Post by Ghost_Mazal on 2011-03-22
Why not just create rsync scripts and add a few crontab entries for them. I have always found that rsync in the end is both the easiest and quickest. With crontab you can create a lot of schedules for the same script.

Just a thought.

---

### Post by nslegacy163 on 2011-03-22
> **Ghost_Mazal said:**
> Why not just create rsync scripts and add a few crontab entries for them. I have always found that rsync in the end is both the easiest and quickest. With crontab you can create a lot of schedules for the same script.

Just a thought.

I'm fairly new to Ubuntu. That's different from the "zip it all" method in the post I linked too, right? I'm assuming the terminal command I can figure out with the manpage?

---

### Post by Ghost_Mazal on 2011-03-22
A very basic example of an terminal rsync command that you can easily put into an executable file:

```
#!/bin/bash
rsync -av /path/to/source /path/to/destination
```

It really is as simple as that.
Rsync will sync your source to your destination and everytime just copy the files that changed and was added , thus saving time.

Once you have your executable script file you go and add crontab entries for it for whenever and how frequent you want it to run the script. Crontab has a lot of options so I would suggest investigating it properly. But here is a very short example:

Open a terminal.
Then type:

```
crontab -e
```

This puts you into editing mode of your actual crontab file.

Add the following line:

```
15 20 * * * /path/to/executablescript
```

Save and exit

That entry means that cron will now execute your script everyday at 20:15pm.

Like already said cron has many options and that is just a basic example.

I find this method much easier and faster for backups than using 3rd party software.

---

### Post by nslegacy163 on 2011-03-22
Awesome! Thank you. I'll give it a go in a bit.

---

