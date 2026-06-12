---
title: "system monitor help!"
date: 2009-07-31
forum: General Help
---

### Post by KegHead on 2009-07-31
Hi!

my system monitor shows i have 245 mb free and 75 mb available.

my system is running slow.

any suggestions on how to free up space?

thanks in advance.

KegHead

---

### Post by aesis05401 on 2009-07-31
What are we measuring here?  If we are talking about RAM then you are running pretty low.  Do you already have a swap partition running?  

If we are talking about hard drive space then you are running *really* low.

Edit: Ah - I see now what you are talking about.  Yes, here are some recommendations:
- Clear local apt cache, run apt cleaning routines
- Find all trash on the system.. there is a tutorial on this site that I am not finding right now about all the places to look for outdated files on Ubuntu... Does someone have a link?
- Check local cache settings for internet browsers
- And if you are getting really low and don't have any other options then you can search for info on removing documentation... I never remove docs - but you can gain a bit of space by doing so.

---

### Post by KegHead on 2009-07-31
Hi!

Thanks for your reply!

I'm hoping to find a terminal apt.

Also, not sure how to clean out firefox cache.

KegHead

---

### Post by aesis05401 on 2009-07-31
On FF - open the 'Edit' menu, choose Preferences, go to Advanced tab.  Under Offline Storage choose the total size of disk space to 'cache' internet pages and files.  Clicking clean will remove the current files that are stored on your machine (these are the same as 'Temporary Internet Files' in Windows).  

As far as apt goes, I am not sure what you mean by hoping to find a terminal apt.  Can you explain that more?

---

### Post by KegHead on 2009-08-01
Hi!

thanks for your replies.

i'm looking for a sudo apt command that might help clear up my ssd.

thanks!

KegHead

---

### Post by YesSir on 2009-08-01
Hi,

I used these tips for my eeepc:

[http://eeebuntu.org/wiki/index.php/Cleanup](http://eeebuntu.org/wiki/index.php/Cleanup)

Worked great for me :)

---

### Post by aesis05401 on 2009-08-01
> **YesSir said:**
> Hi,

I used these tips for my eeepc:

[http://eeebuntu.org/wiki/index.php/Cleanup](http://eeebuntu.org/wiki/index.php/Cleanup)

Worked great for me :)

That is an excellent link.

---

### Post by KegHead on 2009-08-02
Hi!

Thanks for all of your replies!

It's hard to believe but overnight my mini 9 picked up 60 mbs overnight.

Go figure!

KegHead

---

### Post by YesSir on 2009-09-06
Today I used the disk usage analyzer, which told me I have 600 MB in my /home/user/.thumbnails directory, which reminded me of this thread :) Delete! ;)

---

