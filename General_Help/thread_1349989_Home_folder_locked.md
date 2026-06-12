---
title: "Home folder locked"
date: 2009-12-08
forum: General Help
---

### Post by Hermitage on 2009-12-08
Hi all,
nice forum.
I am running Ubuntu 9.04 and the content of my home folder is locked and hidden.
The only stuff in it are a folder with torrents!
My desktop is pretty clean too! Only some folder of documents. No panels,browser,  icons for wireless etc.
I can log in normally, but don't get axcess to anything except for the folders. Can't open the terminal either. I run the computer from the cd now.
Something happend yesterday when I ran upgrades for my programs or downloaded ktorrent I guess. Remember a message in the terminal saying something about home/ and "locked". Maybe I did something stupid, but didn't get any warning
Is this solvable or a fresh install?

I am a newbie, so please be not to technical......

Thanks

---

### Post by Iowan on 2009-12-08
[Here]("http://www.psychocats.net/ubuntu/fixsudo#recoverymode") is a link that may help get into the recovery mode - where you can check your home folder for permissions, etc. Hope that will be a step in the right direction...

---

### Post by Hermitage on 2009-12-08
Thanks for the link, Iowan.
I went into recovery mode and it said I am part of the admin group. So the fault is not there at least.
Do you mean I should do case 2 from the link? If so, what should I write? I really didn't understand from the link. Don't know to much about these things.......

---

### Post by Hermitage on 2009-12-09
Well, I tried case 2. I changed everything so the page look like the one in the link. When I restarted the desktop was the same as before. No visible programs, applications. When I search for a program, like firefox, I can see that it is locked. 
Can only get to the document files on the desktop.

Anybody got an idea of what is going on?

Maybe I should do a reinstall of Ubuntu. Got some backup files of my home folder from before this **** happend..

---

### Post by llamabr on 2009-12-09
If everything is backed up, and this is a fresh install, then a new install will probably solve it, and will take 20 minutes.

In the mean time from a terminal post the output of:

```
ls -l
```

---

### Post by hawthornso23 on 2009-12-09
Are all users experiencing this? Try creating a new user?

---

### Post by Hermitage on 2009-12-09
Thanks guys.
I did list and the only thing that came up was saved stuff from the desktop. But when I did a search in the harddrive I found Firefox, so I know that everything are on the computer, but locked.
Earlier today I installed GRUB because I could not find it in terminal. It did not solve anything, though.
Think it smells more and more of a reinstall.
I only have one user (admin).
I will try to add a new user

---

### Post by Hermitage on 2009-12-09
I added a new user and the desktop is even cleaner! Totally empty.
I'm gonna do a fresh install and figure out how to add everything from my backup.

---

