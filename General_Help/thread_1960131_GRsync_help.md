---
title: "GRsync help"
date: 2012-04-16
forum: General Help
---

### Post by tsinelas30 on 2012-04-16
Anyone using GRSYNC as a automatic back up software on Ubuntu?
  
Share your idea and experience using this.
  
I need to make a case study for GRSYNC.
  
THanks a lot.

---

### Post by CharlesA on 2012-04-16
I'm not using grsync, but I do use plain rsync - it works fine for me.

---

### Post by tsinelas30 on 2012-04-17
> **CharlesA said:**
> I'm not using grsync, but I do use plain rsync - it works fine for me.

Hi sir how can I set scheduled sycn on rsync?
and is it possible to add rsync on start up?

THanks a lot

---

### Post by CharlesA on 2012-04-17
You can schedule tasks using cron, but I am not sure how to add it to start up.

---

### Post by Roasted on 2012-04-17
It's pretty simple. Just tag it as a startup application under the "startup applications" menu.

You have name, command, and comment. I just named mine NAS Backup, and my command is:

```
rsync -az --delete /home/jason/Pictures /home/jason/Documents jason@192.168.1.15:/media/NAS/jason/Desktop
```

That way I rsync my Pictures and Documents to me@fileserver:/location/of/backup/data. Desktop in my destination refers to it being my desktop computer. I do the same for my laptop as well. I have ssh keys set up so when it rsyncs over the network to 192.168.1.15 it doesn't ask me for a password to the file server. I'm already authenticated thanks to the ssh key.

In your case with using Grsync, you can initiate Grsync by doing grsync -e profilename. So if your profile name is backup, grsync -e backup will run it, so that's what you could put in the "command" field.

The difference is, if you use Grsync in startup applications, you'll get an actual GUI output of what happened. I wanted mine to be transparent, so I used old faithful rsync to do it. Every once in a while I log in to the file server remotely to make sure new data transfers over. So far, no issues, and very easy to set up.

[IMG]http://i.imgur.com/xsoLs.png[/IMG]

---

### Post by Roasted on 2012-04-17
> **Jeanne95 said:**
> I'm not using grsync, but I do use plain rsync - it works fine for me.

I really, really think highly of rsync. Grsync is a rather simple GUI that handles rsync flags. If you notice, when you run Grsync, it's simply running the rsync command in the background. I remember being in Grsync and under the menu somewhere there's an option to see the current command it would run with the features you have selected. So realistically, all it does is add a -o to the command when you hit the "preserve owner" checkbox, which -o is the flag for preserving the owner in the man page.

Either way works. I just preferred the transparent method. At any rate, rsync itself is really, really awesome.

I also happen to like the built in backup utility known as Deja Dup. It's an application that a lot of my family members like for quick local backups. I prefer having my raw data backed up without any compression or altering, because often times I refer to my file server from my laptop to drag a document off when my desktop is powered off. Deja Dup is built on Duplicity, which Duplicity uses the rsync algorithm, which might explain why it too is just plain damn awesome. :lolflag:

---

### Post by tsinelas30 on 2012-04-17
> **CharlesA said:**
> You can schedule tasks using cron, but I am not sure how to add it to start up.

OK sir thanks.

Will wait for others input.

---

### Post by tsinelas30 on 2012-04-17
> **Roasted said:**
> I really, really think highly of rsync. Grsync is a rather simple GUI that handles rsync flags. If you notice, when you run Grsync, it's simply running the rsync command in the background. I remember being in Grsync and under the menu somewhere there's an option to see the current command it would run with the features you have selected. So realistically, all it does is add a -o to the command when you hit the "preserve owner" checkbox, which -o is the flag for preserving the owner in the man page.

Either way works. I just preferred the transparent method. At any rate, rsync itself is really, really awesome.

I also happen to like the built in backup utility known as Deja Dup. It's an application that a lot of my family members like for quick local backups. I prefer having my raw data backed up without any compression or altering, because often times I refer to my file server from my laptop to drag a document off when my desktop is powered off. Deja Dup is built on Duplicity, which Duplicity uses the rsync algorithm, which might explain why it too is just plain damn awesome. :lolflag:

Hmmm Deja Dup sounds interesting. Can you give me a link where I can read it.

Thanks

---

### Post by tsinelas30 on 2012-04-17
> **Roasted said:**
> It's pretty simple. Just tag it as a startup application under the "startup applications" menu.

You have name, command, and comment. I just named mine NAS Backup, and my command is:

```
rsync -az --delete /home/jason/Pictures /home/jason/Documents jason@192.168.1.15:/media/NAS/jason/Desktop
```That way I rsync my Pictures and Documents to me@fileserver:/location/of/backup/data. Desktop in my destination refers to it being my desktop computer. I do the same for my laptop as well. I have ssh keys set up so when it rsyncs over the network to 192.168.1.15 it doesn't ask me for a password to the file server. I'm already authenticated thanks to the ssh key.

In your case with using Grsync, you can initiate Grsync by doing grsync -e profilename. So if your profile name is backup, grsync -e backup will run it, so that's what you could put in the "command" field.

The difference is, if you use Grsync in startup applications, you'll get an actual GUI output of what happened. I wanted mine to be transparent, so I used old faithful rsync to do it. Every once in a while I log in to the file server remotely to make sure new data transfers over. So far, no issues, and very easy to set up.

[IMG]http://i.imgur.com/xsoLs.png[/IMG]

Thanks for this.

Will try it and give update once OK.

---

### Post by Roasted on 2012-04-18
> **tsinelas30 said:**
> Hmmm Deja Dup sounds interesting. Can you give me a link where I can read it.

Thanks

Deja Dup is built into Ubuntu and I believe Fedora. If you go into System Settings, it's labeled "Backup". It's a very, very easy utility to use. It has options for backing up to another local drive, a samba share, ssh directory, etc. 

I would advise quite a few users out there to use Deja Dup, but it really depends on the scenario. For example, I set up a backup server at my parents house, but their systems rsync to it, not Deja Dup to it. I did this for a reason. In an effort to save them a few bucks BUT have an active backup of their data, I set the system to turn on once a day for 1.5 hours at a time, then gently power off. I did this with the help of a 25 dollar surge strip that has 2 ports set on a timer. With a quick BIOS setting (turn on when power connected), it kicks on just then.

Now, Deja Dup synchronizes new data over, again in 10.0MB slices. The curve ball is, in an effort to ensure maximum data integrity, Deja Dup will "re-do" the backup every once in a while. If the server was running 24/7, I'd be okay with that, but since I only have a 1.5 hour window, I wanted to ensure maximum speed. So... rsyncing the raw data was the way to go. That way if Deja Dup was set up and it decided to do a new backup I wouldn't be racing against time. What if a fresh Deja Dup backup needs 2 hours to run but the server is only set up for 1.5 hours a day? That's why I chose what I chose. After all, computers don't take up much power versus a microwave, but every penny counts, so saving 22.5 hours of uptime a day wasn't a bad route to go. 

I set the clients up via cron to run the command at 7PM every day... while the server turns on at 6:50PM every day. Then at 8:30, cron shuts the system off, and midnight the power is cut from the port (so if I need to remote in and update it, I can lift the 8:30 shutoff entry if it needs more time updating).

Deja Dup is a really incredible application, with a ton of respect also going to Duplicity (which it's based on) as well as rsync, the algorithm it utilizes.

---

