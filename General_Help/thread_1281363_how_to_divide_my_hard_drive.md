---
title: "how to divide my hard drive?"
date: 2009-10-03
forum: General Help
---

### Post by kboy on 2009-10-03
HI, i've been using ubuntu for a while now. I've always partitioned my hard drive the same way.
I have a 500 GB drive with only ubuntu installed, a partition for my movies, another one for music, and two others for the root and home directories.

I was wondering if there is a more efficient way of partitioning, maybe having only two partitions (root and home) is better?

i would appreciate any advice, thanks.

---

### Post by wojox on 2009-10-03
Sure, I give 10 G to root and the rest to home on a 200 GB HDD. Seems to work alright. 10 G to root maybe a little overkill, but I never know.

---

### Post by jward3010 on 2009-10-03
To be honest, there's nothing INefficient about your particular setup, more complicated than usual, yes, but not ineffiecient.

In a sense it seems you have particular needs in the way that you have separate partitions for music and videos. Any particular reason? 

I'd say a safe partitioning model would be:

1st - 5GB for "/" (root)
- this enables space for OS and most importantly updates which need to extract themselves and expand, also a decent amount of /tmp space for apps that need it. If you do DVD burning / authoring increase this to maybe 10GB.

2nd - 2 X RAM for swap
- If you don't have this set up do it whenever you're changing, swap is important for memory spillover if some particular apps are hungry on memory. It should be at least the size of your RAM minimum, preferably twice the size.

3rd - the remainder for /home
- I'd dump all your videos and music in here. This is pretty much as safe as having those above separated.

---

### Post by kboy on 2009-10-03
I'm just a bit used to the windows partitioning which usually had a few drives like C, D, E....
and on D i would save my movies for example.

another question is when install a new version of ubuntu what happens to my home partition??

---

### Post by jward3010 on 2009-10-03
> **wojox said:**
> Sure, I give 10 G to root and the rest to home on a 200 GB HDD. Seems to work alright. 10 G to root maybe a little overkill, but I never know.
Depending on what you do, I find the biggest gulpers of space are things that need /tmp for only a few minutes but for large files such as Brasero, DeVeDe, Disc burners and if you do stuff related to DVD's - whether making or burning big ISO's you'll need a generous amount of space. So 10GB is actually a good idea in that regard

If not stick to around 5GB for "/", 4GB if small drive (like a 40GB or 60GB).

---

### Post by jward3010 on 2009-10-03
> **kboy said:**
> I'm just a bit used to the windows partitioning which usually had a few drives like C, D, E....
and on D i would save my movies for example.

another question is when install a new version of ubuntu what happens to my home partition??
You're /home partition will be utilised on next install if you decide to mark it as your /home partition during the partitioning stage of the next install. Pick the partition during the partitioning section of the install and set it to /home from the drop down menu - DON'T SELECT THE FORMAT OPTION. It will basically use your OLD /home as the NEW /home. 

All your system settings and configuration is saved in /home in hidden files and folders so your system will be almost identical when it starts up again even though it's a fresh install. If you want to start afresh go into /home/username, press Ctrl+H to show hidden items and delete them all.

---

### Post by cguy on 2009-10-03
What if you have multiple users?
Will it recognize the multiple home folders and automatically create the accounts?

---

### Post by XCan on 2009-10-03
Yes, since the home folders of each user reside in /home/username and the mount point points to /home. That being said, with hdd in abundance, I would go for 10GB for / to be safe. I don't have much installed and am sitting at 3.9GB in my /, sure 5GB could work, but as mentioned, /tmp/ or /var/ can fill up suddenly sometimes.

---

### Post by cguy on 2009-10-03
Do you speak from experience?

After reading about useradd ans /etc/passwd, I am having doubts everything goes so smooth. I want to hear from someone who actually did this.

---

### Post by jward3010 on 2009-10-03
I have done it and it worked, in fact it annoyed me as I wanted a completely fresh install and instead found myself booting into the same system with the same wallpaper and everything, I coincidentally left the username the same and it all just happened without cribbing or bitching.

NOTE: I have NOT tried it with multiple accounts but why it should be any different from above... Do everything with an experimental mindset or wait around for a better answer.

---

