---
title: "Removing packages from a failed install attempt"
date: 2012-02-12
forum: General Help
---

### Post by grey1beard on 2012-02-12
I'm running Natty on a 32 bit laptop, and I'm trying to get LinuxCNC to install in sim mode.

In doing so, I've tried several methods, and consequently got various packages now loaded that are not needed.

So that I can be sure (?!!) that nothing interferes with further attempts, I'd like to know if "sudo apt-get autoclean" or similar will get rid of the debris I've aquired.

If not, is there a way of identifying them, possibly by recent date, and picking out the pieces by hand ?
I'm looking for a general method, and only using this case as an example of how often I mess up. :)

John

---

### Post by savanna on 2012-02-12
I would do a '**dpkg -l > start.txt**' before starting such adventures (to list package statuses).

After *said adventures* you could then do a '**dpkg -l > end.txt**' and do a diff on the files, to find what's changed. You could then even write a little shell script to remove the added packages - "man diff" will give you lots of options for making it easier to read the output in a script.

---

### Post by grey1beard on 2012-02-12
Thanks, savanna, that looks neat, and I'll try to remember next time, before I start.

I've just had a quick read of man diff, and I get the idea that this will compare the contents of named files, rather than what I assume may be a case of "hunt the thimble(s)"?
I've not had the pleasure of writing scripts yet, so it would be a hesitant newbie venturing in that direction.

Regards
John

---

### Post by jacob.david on 2012-02-12
[FONT="Verdana"] sudo apt-get autoclean will only remove the .deb files located under /var/cache/apt/archives that are not installed. But in your case it appears like you have already installed the packages. So you will have to manually remove the unwanted packages.
You may also try sudo apt-get autoremove. This command removes packages that were installed by other packages and are no longer needed [/FONT]

---

### Post by grey1beard on 2012-02-12
Thanks, jacob.david, another addition to my armoury, or perhaps "broom in the closet", might be better !

A major part of the problem is identifying what and from where I need to remove the junk.

Regards
John

---

### Post by savanna on 2012-02-12
> **grey1beard said:**
> Thanks, savanna, that looks neat, and I'll try to remember next time, before I start.

You're welcome :D

> **grey1beard said:**
> 
I've just had a quick read of man diff, and I get the idea that this will compare the contents of named files, rather than what I assume may be a case of "hunt the thimble(s)"?

That's the purpose of doing the **dpkg -l > start.txt** before starting, and **dpkg -l > end.txt** after finishing - you could compare the two files using diff.

> **grey1beard said:**
> 
I've not had the pleasure of writing scripts yet, so it would be a hesitant newbie venturing in that direction.


I've got to run off to work now - Monday morning - when I get a chance I might whip up a script...

---

### Post by grey1beard on 2012-02-12
Thanks Sonia, and to make sure we are not at cross purposes, I do understand the usefulness of using your suggestion.

However, the focus of my present problem is that I don't know the consequences of my earlier actions.

I've downloaded two debian packages and a shell script, and while composing this, I've just realised that they will be in my Downloads folder.

If I click on the first of them, it sends me to the Software Centre, and informs me that it is the wrong architecture - 64 bit - not for my 32 bit laptop, so I know that this can be removed, and should not have left anything behind.

The second debian package also points me to the software centre, but this window then closes with no apparent effect.

Finally the script file, which I tried to run, but I've since discovered it  doesn't work in Natty. 
[Apparently the installed python version isn't backward compatible with the emc2-sim(the software I'm trying to install), and this is where the original problem lies.] 
My elderly memory can't recall the sequence of events while running the terminal that might tell me what occurred.

If nothing was installed/removed, all well and good, and if my line of enquiry on another forum gives me a workaround to get emc2-sim to run, I can safely assume that there should be no problems of my own making.

Regards,

John

---

