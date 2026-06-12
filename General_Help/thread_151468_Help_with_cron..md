---
title: "Help with cron."
date: 2006-03-28
forum: General Help
---

### Post by frost_ad on 2006-03-28
Hi.
I've never set up a cron job before but I have a need for one now and need some help. Everyday at 3:30pm I need to create directory with a name and the current days date (name_03282006 or something similar) I then need to move the contents from another directory into the newly named one. Are there any experienced cron people out there that can help me?

---

### Post by open_sauce on 2006-03-28
I can get you half way there...

This gets you in to edit the cron tab
> crontab -e 

And this line would run every day at 3:30pm --
> 30 15 * * * mkdir /home/yourusename/new_directory


Then you can copy stuff in 2 mins later with:

> 32 15 * * * cp -r /home/yourusername/sourcedir /home/yourusername/new_directory


....but someone will come up with an elegant 1-liner that does the date in the directory and the copy of source files in one elegant move, probably.

Crontab example [here]("http://www.adminschoice.com/docs/crontab.htm")

---

### Post by frost_ad on 2006-03-28
Cool. I guess I don't necessarily "have" to have the date but I wouldn need it to count or somehow distinguish the different directories. 

Thanks for your help!!

---

### Post by frost_ad on 2006-03-28
Just in case anyone else needs to do this I figured out how the command for making a directory with the current date in it.

```
mkdir $(date +%Y-%m-%d)
```

That would give you a directory that was called 2006-03-28

---

