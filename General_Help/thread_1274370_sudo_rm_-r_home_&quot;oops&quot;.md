---
title: "sudo rm -r /home// &quot;oops&quot;"
date: 2009-09-24
forum: General Help
---

### Post by Josepie on 2009-09-24
So.. as you can see, I did the worst thing. Is there a way to undo or restore this? I am kind of a noob with Linux. 

I have a T60 laptop with Ubuntu 9.04 Jaunty Jackalope which I have been running for about 6 months now. I was at the latest update. I did backup my important files but its the stuff like virtualbox and etc that I would love to get back. 

Any help is appreciated.

---

### Post by compiledkernel on 2009-09-24
Uh....there is very little hope of that. I can certainly hope you had backups.

---

### Post by jonobr on 2009-09-24
Hello

The only thing close that I can think of is to login to the console
ctrl-alt-F1

and then create a new user on the command line.

Im guessing you cant login at the moment, so I think creating the new user will create a new home folder. Your personal stuff not backed up is gone AFAIK.

---

### Post by Josepie on 2009-09-24
I can still login. Its just all my personal stuff is gone.

---

### Post by jonobr on 2009-09-24
Thats a bonus!

so if it isnt in the trash, compiledkernel's post still applies

---

### Post by Josepie on 2009-09-24
Oh well, thanks guys! Guess I need to rebuild again.

---

### Post by NewlyHuman on 2009-09-24
> **jonobr said:**
> Hello

The only thing close that I can think of is to login to the console
ctrl-alt-F1

and then create a new user on the command line.

Im guessing you cant login at the moment, so I think creating the new user will create a new home folder. Your personal stuff not backed up is gone AFAIK.

Nothing except the user's data is stored in the home directory. /etc/passwd and /etc/shadw are where the user credentials are stored.

> **Josepie said:**
> I can still login. Its just all my personal stuff is gone.

When deleting, files aren't actually erased. The inodes are merely wiped - They store information about files and directories. This is why you can remove files much faster than your hard drive is actually capable of writing data.

However, this isn't much. Every time you use the partition, you risk using and  overwriting space that your data used to occupy. You could make an image of the drive, but unless you have *critical* documents that you need to recover, don't bother.

The best you can hope for is a copy of all your data - But it will lack filenames, directory structure, etcetera - A mess, in other words.

If you haven't got anything critical on the partition, I would just take this as a harsh lesson in recursive deletion and move on.

---

### Post by Josepie on 2009-09-24
Yes, harsh lesson indeed. 

To be fair to myself, I did have backups of some of my important files. Not a total loss I guess.

---

### Post by jonobr on 2009-09-24
Hats off to you,

Most posts like this people usually dont.

Kudos

---

### Post by ibuclaw on 2009-09-24
If you have a separate home partition, you could use **testdisk** to see what you could recover.

General steps are as follows:
[LIST=1]
[*]Run a deep search on your hard drive
[*]Highlight the partition that contains the deleted files and press **P**
You will be shown a directory view of what is on that partition (what is highlighted in [COLOR="Red"]red[/COLOR] is a deleted item.
[*]Browse to the location of the deleted items with the arrow keys. (Right is traverse into directory, Left is to come out of. Up and down are to scroll through the files in the directory).
[*]Select the deleted files and recover them to a location that is preferably on another hard drive
[/LIST]

Regards
Iain

---

