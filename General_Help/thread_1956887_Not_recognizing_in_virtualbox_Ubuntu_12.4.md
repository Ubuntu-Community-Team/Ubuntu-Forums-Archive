---
title: "Not recognizing in virtualbox Ubuntu 12.4"
date: 2012-04-11
forum: General Help
---

### Post by ran1wil on 2012-04-11
I have virtuabox installed on ubuntu 12.4 running xp asthe guest OS with the guest additions installed and the extension packs. I know that in previous versions of ubuntu i had to add myself as a user of virtual box group to get it to work but in the new version i cant figure out how to do that if that is what i need to do....A little assistance please

---

### Post by PhantomTurtle on 2012-04-11
In Ubuntu 12.04 Users and Groups are not installed by default, so install it using,
```
sudo apt-get install gnome-system-tools
```
in terminal.
Then go to System Setting --> Users and Groups --> Manage Groups. Find "vboxusers", click properties, check the box with your username on it and click on. I'm not sure if it requires a restart or not(probably doesn't). Also, it's Ubuntu 12.04 not 12.4.

---

### Post by ran1wil on 2012-04-11
thanks for the quick response i will give it a try tonight and post my progress and yes 12.04 sorry my mistake

---

### Post by PhantomTurtle on 2012-04-11
> **ran1wil said:**
> thanks for the quick response i will give it a try tonight and post my progress and yes 12.04 sorry my mistake

Sorry about posting that 12.04 thing, I'm just very picky about it since a lot of people do it wrong, but they don't get it wrong on purpose and neither did you.

---

### Post by ran1wil on 2012-04-11
No problem im just happy for the fast and correct response. everything you told me worked perfectly my machine is working again thank you

---

