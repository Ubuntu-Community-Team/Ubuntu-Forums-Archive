---
title: "Mounting hard drives"
date: 2009-11-26
forum: General Help
---

### Post by Scooter_X on 2009-11-26
Hello,

I am running Karmic, and have partitioned my drive into basically having 60gb for Windows 7, 20gb for Ubuntu and whatever was left over for storage. 

Here's my question:  Can I "auto-mount" those on startup? Every time I restart the computer, if I want access to them, I have to go to the 'Places' menu and click on them and then have to put in my password. But I want to be able to link to folders that are in those drives and use them as 'documents' and 'pictures' folders instead of the ones in the places menu. It's not the worst thing in the world having to mount them manually each time, but does anyone know if I can have them automatically mounted instead of having to go through the tedious task of mounting every time? Thanks.

---

### Post by audiomick on 2009-11-26
You can. you have to edit /ect/fstab
You have to determine the UUID of the drives, and add them to the list in there
I'm sorry, but I am too shaky on the "how" to attempt to guide you through it.

---

### Post by akakingess on 2009-11-26
Try this link [http://ubuntuforums.org/showthread.php?t=785263&highlight=automounting](http://ubuntuforums.org/showthread.php?t=785263&highlight=automounting) or do a search on FSTAB as that is where entries for automounting are going to end up anyway.

As far as the UUID, yes you may need those, which I think you can get just by running GParted, but don't actually change anything from within there.

---

### Post by Grenage on 2009-11-26
You don't _need_ the UID, but it is the better way of doing it.

---

### Post by akakingess on 2009-11-26
> **Grenage said:**
> You don't _need_ the UID, but it is the better way of doing it.
Yeah, that's why I say you MAY need them, there are actually I think 4 different ways to do it, one being with the UUIDs.

BTW: Grenage, that was not meant to be argumentative, actually more agreeing with you, please don't take it the wrong way...

---

### Post by Grenage on 2009-11-26
> **akakingess said:**
> BTW: Grenage, that was not meant to be argumentative, actually more agreeing with you, please don't take it the wrong way...

Oh no, I won't; you are quite correct. :)

---

### Post by Scooter_X on 2009-11-26
BooYA! Thanks, akakingess for the link! Works! Solved! :D

---

### Post by akakingess on 2009-11-26
> **Scooter_X said:**
> BooYA! Thanks, akakingess for the link! Works! Solved! :D

Great to hear, now if you don't mind marking this thread as "SOLVED", that way others won't look in to try to help, or others with the same problem can see that you had it and got it resolved. Thank you for doing this, it helps the overall forum process.

BTW:  I believe that you do it through Thread Tools, and since you are the OP (Original Poster), you are the only one allowed to mark it as solved.

---

### Post by Scooter_X on 2009-11-26
I totally understand. Got it. Thanks. :D

---

