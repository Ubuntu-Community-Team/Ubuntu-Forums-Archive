---
title: "Help with advanced copy command in terminal"
date: 2011-04-14
forum: General Help
---

### Post by willcoq on 2011-04-14
I work in a tech shop, and I'm using a live USB of Ubuntu to copy files from a customer's old, failing hard drive onto their new hard drive. Specifically, I just need several folders from the Users directory of their Vista installation.

I need to copy Contacts, Desktop, Documents, Downloads, Favorites, Links, Music, Pictures, Saved Games, and Videos from Users\Jacob on the old drive to Users\Owner on the new drive. I attempted this via the GUI, but it asked me if I wanted to Retry or Skip Files every time it encountered an I/O error. Of course I want to Skip, but I have no option to "Skip everytime there is an I/O error." There are a lot of errors because the old drive is in bad shape. I spent 4 hours yesterday clicking "Skip" every 15 seconds. It was agonizing.

The old drive is /dev/sdc1 and the new drive is /dev/sda1.

What is the proper copy command to exclude files that won't copy due to an I/O error?

---

### Post by WorMzy on 2011-04-14
Not something I've ever done myself, but have you looked at rdd-copy?

[http://manpages.ubuntu.com/manpages/maverick/en/man1/rdd-copy.1.html](http://manpages.ubuntu.com/manpages/maverick/en/man1/rdd-copy.1.html)

Looks like it may be of use to you.

---

### Post by willcoq on 2011-04-14
From what I can gather, rdd-copy will copy the bad files over, but they will be unusable. I may be wrong about that. I'd rather just skip the files if there is an I/O error.

Fortunately, I was making things FAR to difficult. Here's what I'm doing now:

I mounted the old, bad drive to /media/old and the new drive to /media/new, and used the following standard command:

cp -r /media/old/Users/Jacob/Contacts /media/new/Users/Owner

As it's copying, it tells me "cp: cannot stat 'filename': Input/output error" and goes on to the next file, skipping the one it couldn't copy.

It's working well so far, and I just rename Contacts to Desktop, run it again, and so on.

Thanks for the help! I think I'll stick with this method for now.

---

### Post by seawolf167 on 2011-04-14
> **willcoq said:**
> cp -r /media/old/Users/Jacob/Contacts /media/new/Users/Owner


Came here to suggest to see if this would work. You could also add a wildcard to copy all folders from the parent folder like so:

```
cp -r /media/old/Users/Jacob/* /media/new/Users/Owner
```

---

