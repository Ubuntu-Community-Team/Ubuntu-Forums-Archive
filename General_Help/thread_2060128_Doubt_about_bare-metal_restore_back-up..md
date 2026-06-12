---
title: "Doubt about bare-metal restore back-up."
date: 2012-09-19
forum: General Help
---

### Post by newhere_m on 2012-09-19
I have never created back-up of my operating system and personal files and need to clear my doubt regarding this. I guess, in case I create bare-metal back-up, using say redo, I need to save the backup image in a dvd. But what happens if the size of the file exceeds the capacity of the dvd? Can I use more than one dvd to create entire back-up? If so, is there any special step to perform?

---

### Post by thnewguy on 2012-09-19
I suppose you could backup your system files onto one DVD and then put your personal files onto a series of DVDs. Though after a certain amount of data you are going to hit a point where it is more cost effective (and much more time effective) to purchase an external hard drive, rather than burning additional DVDs.

---

### Post by vandorjw on 2012-09-19
Something far more effective is to backup only your configuration files.

```

# find / -iname *.conf

```**Please not that this command doesn't copy or make a save. It only shows locations of files.

The binary files can always be downloaded from the repositories.
This can save quite a bit of space.

As well, instead of backing up all .configuration files, you can check to see if you changed any and only backup the onces you changed.

```

diff file1 file2

```

I haven't looked but I am sure there are programs/bash scripts that automate this.

**[joke]**
Your personal data should be stored on Facebook where Mark Zuckerburg will take good care of it.
**[/joke]**

Personal documents and Music go on external hdd

---

