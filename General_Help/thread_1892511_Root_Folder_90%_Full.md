---
title: "Root Folder 90% Full"
date: 2011-12-08
forum: General Help
---

### Post by Katla on 2011-12-08
I've looked around the internet for answers to this, and while I've found plenty of documentation, I'm having a hard time seeing anything in plain language. Basically, I think I need my hand held a bit on it. I'm pretty new to Linux. 

I'm using Natty 11.04, installed about 3 months ago. While I was making disk partitions I used what advice I could find, and made my root partition 7 GB. From what I saw then and have read since, that should have been plenty. However, almost immediately it filled up. At one point it was so full I couldn't even log in after shutting down and it took me forever to finally figure out that I needed to go into the terminal and run autoclean. 

Right now I've got 675 MB free in that partition, and that's with using the clean command as well as the advice in [this thread]("http://ubuntuforums.org/showthread.php?t=140920&highlight=root+folder+full"). I'd like to install Ocelot 11.10, but don't have the room to do it. And what free space I have in there is steadily disappearing.

The "easy" answer is to save everything and reformat the disk. Give myself, say, 50 GB or something crazy for the root. But in everything I have read it seems that I've got plenty of space as it is. I mean, really, how much space does an OS need? There's just something hogging it. 

I'd appreciate it if I could get some troubleshooting help with this. Advice on how to get into my root folder to see what the culprit may be, and/or feedback on what steps I can take to ensure this isn't a problem after any changes I make. 

Thank you.

---

### Post by nothingspecial on 2011-12-08
It could be that you have a repeated error that is generating multiple logs.

Have a look in /var/log

Of course if that is what's causing the issue then it will quickly fill up again and you will need to fix the underlying issue.

---

### Post by Katla on 2011-12-08
No, that's not it. I'd checked the log folder after reading about it in my investigation, but it's only got 4.4 MB in it. Probably still bloated for logs, but not what's causing the issue.

---

### Post by nothingspecial on 2011-12-08
What is the output of ```
du -hx --max-depth=1 / 2>/dev/null

```

---

### Post by Katla on 2011-12-08
How do I paste into the terminal? I've tried both Ctrl+Shift+V and Shift+Insert to no avail.

---

### Post by Katla on 2011-12-08
The one thing that stands out with that command is 5.2 GB in /usr.

3+ gigs within the Share folder in /usr. Not sure if that's relevant.

---

### Post by WorMzy on 2011-12-08
7GB for / is fine, if you don't try to install every application under the sun, and store your personal files on another partition. With a fresh install of Natty, you should be looking at about 2.6GB in /, with 1.9GB worth of files in /usr.

I recommend that you uninstall some applications that you don't need.

---

### Post by Katla on 2011-12-08
Within /usr/Share I've got 2.3 GB in the Games folder. I can delete almost all of those, as they're not very interesting and I installed them mostly out of curiosity. Seems odd that they'd wind up in there, though.

---

### Post by Katla on 2011-12-08
OK, with most of the games removed I've now got 2.6 GB available in /. 4.3 GB used. Still some bloat, but at least now I should be able to upgrade and have an idea of the problem. If anyone has any advice as to what else may be eating up space, I'm all ears. Otherwise, I very much appreciate the tips given.

---

### Post by nothingspecial on 2011-12-08
Yep, you just had to many applications :)

---

### Post by WorMzy on 2011-12-08
Indeed. If you'd like to install lots of applications at once, then a bigger / would be the best way to go about it. Depending on the placement of your partitions, gparted should be able to resize / without much trouble -- from a liveCD/USB. 50GB would be a bit overkill in my opinion though, unless, of course, you have several terabyte drives at your disposal. :P

---

### Post by Katla on 2011-12-08
I won't need to use gparted. Now that I know that those applications are staying in / I can avoid the issue. Basically, when I first got Ubuntu I was going around installing whatever app sounded nice, regardless of whether or not I really wanted/needed it. I figured this or that might come in handy, etc. And if it were being stored on the free part of my drive, that'd be OK. Lots of space there. As it is, it isn't a problem for me to slim down, installing things on a basis of necessity. 

Thanks again for clearing this up for me. It seems so simple now, but things usually do after the fact.

---

