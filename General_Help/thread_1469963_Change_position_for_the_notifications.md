---
title: "Change position for the notifications"
date: 2010-05-02
forum: General Help
---

### Post by durus on 2010-05-02
How can I change the positions for the notifications? 
It is at a weired place after installing 10.4 and I need to move it. 
I have been googling about it and it seems like the position is hard coded in the source code, can this really be true? If it is, I am starting to question my decision to use Ubuntu. How can i serous skilled developer hard code something like that in the source code? Can I trust the developer to know what he is doing?
Please tell me that it is possible to change something so fundamental as that.
Thank You.

---

### Post by sparker256 on 2010-05-02
> **durus said:**
> How can I change the positions for the notifications? 
It is at a weired place after installing 10.4 and I need to move it. 
I have been googling about it and it seems like the position is hard coded in the source code, can this really be true? If it is, I am starting to question my decision to use Ubuntu. How can i serous skilled developer hard code something like that in the source code? Can I trust the developer to know what he is doing?
Please tell me that it is possible to change something so fundamental as that.
Thank You.

If we are talking about the same thing right click and click on the move selection.

Bill

---

### Post by P4man on 2010-05-02
Maybe this helps:
[https://answers.launchpad.net/notify-osd/+question/80515](https://answers.launchpad.net/notify-osd/+question/80515)

---

### Post by durus on 2010-05-03
> **P4man said:**
> Maybe this helps:
[https://answers.launchpad.net/notify-osd/+question/80515](https://answers.launchpad.net/notify-osd/+question/80515)

This is ridiculous, this seems to have been requested for a long time and it is so easy to implement. I can't even understand how a developer can hard code this stuff and how can the ubuntu team use something like this instead of modify it. It would probably take them less than 1 hour with testing and everything if they know what they are doing. I really hope they know how to do so simple things.
The funniest thing is that people has been written patches that does this, why does not the ubuntu team implement them?

I have heard about proud people within the open-source community can this be the case here? That they want to be able to decide everything for you instead of letting the user decide how they want to use the applications?

---

### Post by P4man on 2010-05-03
I agree its rather weird, but I will give them the benefit of the doubt when it comes to being **able** to use parameters here. I think canonical has a rather good idea where they want to go with the UI, the notification popups is just one aspect of that, the new indicator menu's and the announced "windicators" are all pointing in the same direction, and perhaps they dont want to encourage people to set things up or develop apps/themes etc that will break in 10.10 and future versions as they implement those GUI changes.

Of course its all opensource, so nothing prevents you from changing it, but at least then one cant complain if stuff breaks when upgrading to 10.10 or 11.04

At least this is my guess. Cant see another reason

---

### Post by wojox on 2010-05-03
Go here and download or add the repo [https://edge.launchpad.net/~gilir/+archive/updates/+packages](https://edge.launchpad.net/~gilir/+archive/updates/+packages)

Then you want notify-osd (0.9.29-0ubuntu3~gilir2) lucid

---

