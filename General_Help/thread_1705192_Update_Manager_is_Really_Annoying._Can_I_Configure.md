---
title: "Update Manager is Really Annoying. Can I Configure it?"
date: 2011-03-11
forum: General Help
---

### Post by ChannelZ28 on 2011-03-11
i really dont like having to update all the time, especially things i dont want. i can uncheck them, but they just show up in the next update. there is also software that comes with ubuntu, that i dont want. for example, Empathy and Gwibber. i dont know what they are and i have no interest in ever using them. i do have interest in the space they take up on my drive, considering i only have 16gb.

i can remove them, but then they just show up in the update manager. not only is it annoying to have it pop up each time i log on, but if i keep unchecking things i dont want, it would soon take about a week to go through the list each time i start my computer to determine what i want and what i dont.

is there some way that i can reconfigure th update manager to remove anything from the list that i uncheck? that would be really cool.
thanks.

---

### Post by PoHandle on 2011-03-11
This is very possible, though I haven't really ever done this for anything except kernel updates.  I can't say how it will affect other software.

What you want to do is create a list of the packages that you do not want to update.
Make sure to record the package's name, and not it's title. (eg: *chromium-browser* not *Chromium Web Browser*)
Next, open up Synaptic Package Manager (System > Administration > Synaptic Package Manager)
Search for each package on your list, highlight it, then click Package > Lock Version.

You can also remove unwanted packages using Synaptic as well.  Just click on the box to the left of a package's name and click "Mark for Removal".  You can also use "Mark for Complete Removal" to remove any associated configuration files as well.

---

### Post by ChannelZ28 on 2011-03-12
hey thanks, that works. can you explain to me why? what does the lock actually mean?

---

### Post by SavageWolf on 2011-03-12
You should update everything, if you don't you are leaving your system open to security flaws. For programs that you don't know what the are, and don't need, just go to the Software Centre and search for them, if they have an icon they should be safe to remove. If they look like a cardboard box with stuff in, they may be critical OS programs, so check first.

Updating a program doesn't make it take up any more disk space.

---

### Post by jerome1232 on 2011-03-12
I just wanted to note that if you remove a program you will not get prompts to update it, the programs you do have you should keep updated, these aren't feature improvements your getting, they are security updates and bug fixes. That means there are flaws in the programs and these updates fix those flaws.

Also as noted above an update won't necessarily take up more space, it can take up a little more but it can actually take up a little less too.

---

### Post by ChannelZ28 on 2011-03-16
thanks for the replies. i always try to check out what each update is before i download it. more to learn something than to decide if i need it or not.

just to clarify, when i download a security update, it overwrites the old data, thus not taking up any more space on my drive?

---

### Post by PoHandle on 2011-03-29
It really depends on the update.  Generally, yes, an update will overwrite older data, though there are exceptions to this rule.  If you are concerned with disk storage related to updates, be sure to run
```
sudo apt-get clean
```
which will remove the downloaded packages from your cache.

---

