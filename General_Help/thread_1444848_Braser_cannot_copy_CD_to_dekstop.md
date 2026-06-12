---
title: "Braser cannot copy CD to dekstop"
date: 2010-04-01
forum: General Help
---

### Post by altjx on 2010-04-01
I opened Braser, clicked Copy Disc... I'm trying to copy my CD to an ISO file on my Desktop. Instead, it says this

```
The image could not be created at the specified location. Do you want to specify another location for this session or retry with the current location?
You do not have the required permissions to use this drive.
```

The hell is this?

---

### Post by blueridgedog on 2010-04-01
Can you create the image in another location, say in /home/USER where USER is your user name?

---

### Post by altjx on 2010-04-01
> **blueridgedog said:**
> Can you create the image in another location, say in /home/USER where USER is your user name?

Nope, I get the same error

---

### Post by blueridgedog on 2010-04-01
Some random questions then:

-are you certain you have enough free space?

-can you create files in your home directory/on your desktop with other applications?

-do you get the same error if you select and ISO or a readcd image type? (click properties, then disk image type at the bottom).

---

### Post by altjx on 2010-04-01
> **blueridgedog said:**
> Some random questions then:
 
-are you certain you have enough free space?
 
-can you create files in your home directory/on your desktop with other applications?
 
-do you get the same error if you select and ISO or a readcd image type? (click properties, then disk image type at the bottom).
 
I have over 80GB of free space.
I can create files manually in all of the areas of which I try to burn my ISO file.
I've only tried changing it to ISO since that's the file type I wanted to use.

---

### Post by blueridgedog on 2010-04-01
The only information I could find was this threat regarding mint Linux:

[http://forums.linuxmint.com/viewtopic.php?f=47&t=27852](http://forums.linuxmint.com/viewtopic.php?f=47&t=27852)

Do you get any more descriptive error if you run brasero from the command line and then attempt the copy (looking for errors that output in the terminal used to launch brasero)?

Do you also get the same result with other CDROMs?

---

### Post by altjx on 2010-04-01
> **blueridgedog said:**
> The only information I could find was this threat regarding mint Linux:
 
[http://forums.linuxmint.com/viewtopic.php?f=47&t=27852](http://forums.linuxmint.com/viewtopic.php?f=47&t=27852)
 
Do you get any more descriptive error if you run brasero from the command line and then attempt the copy (looking for errors that output in the terminal used to launch brasero)?
 
Do you also get the same result with other CDROMs?
 
Haven't tried with another CD, I'll let you know what happens. Also, when I tried running braser as root in terminal, it did come up with a big list of text in the terminal, but then it went away. I'll post as soon as I switch back over to linux. I needed to get it done quicker so I had to switch to windows really qiuck.

---

### Post by altjx on 2010-04-02
Well, after switching back over to Ubuntu 10.4 (been using this one for awhile), everything's fine again, lol. thanks for the help with troubleshooting =)

---

