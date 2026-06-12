---
title: "Installed Thunderbird 3 with Ubuntuzilla, can't find profile"
date: 2010-01-22
forum: General Help
---

### Post by caro on 2010-01-22
I used Ubuntuzilla to install Firefox 3.6 and Thunderbird 3.0. FF worked perfectly but T'bird doesn't see my profile with all my mail, server settings, etc.  I really don't want to reconfigure them if I can avoid it.

I tried moving the contents of my Thunderbird 2 profile's mail folder (in .mozilla-thunderbird) to my Thunderbird 3.0 profile (.thunderbird) but it didn't make a difference.  Is this a permission problem or is something I'm missing?

---

### Post by Tanker Bob on 2010-01-22
> **caro said:**
> I used Ubuntuzilla to install Firefox 3.6 and Thunderbird 3.0. FF worked perfectly but T'bird doesn't see my profile with all my mail, server settings, etc.  I really don't want to reconfigure them if I can avoid it.

I tried moving the contents of my Thunderbird 2 profile's mail folder (in .mozilla-thunderbird) to my Thunderbird 3.0 profile (.thunderbird) but it didn't make a difference.  Is this a permission problem or is something I'm missing?

I'm on Karmic x86_64 though, and used the Mozilla daily PPA repository which installed TB 3.0.2, rather than Ubuntuzilla. On my system, TB 3 used .thunderbird-3.0 for its profile. Does that exist on your system? TB 3 picked up my TB 2 profile and imported everything over to the new installation automatically. I'm not sure why yours didn't. There may be some difference in the builds, or perhaps a bug in TB 3.0. 

Did you try to import your old info into TB 3 using the Tools -> Import... wizard?

---

### Post by caro on 2010-01-23
> **Tanker Bob said:**
> I'm on Karmic x86_64 though, and used the Mozilla daily PPA repository which installed TB 3.0.2, rather than Ubuntuzilla. On my system, TB 3 used .thunderbird-3.0 for its profile. Does that exist on your system? TB 3 picked up my TB 2 profile and imported everything over to the new installation automatically. I'm not sure why yours didn't. There may be some difference in the builds, or perhaps a bug in TB 3.0. 

Did you try to import your old info into TB 3 using the Tools -> Import... wizard?

There isn't a .thunderbird-3.0 on my system.  I did try using the import wizard but it didn't see anything.  I guess I could try to uninstall TB 3, go back to TB 2, export the files, and then start over and try to use the wizard but I'd rather not if I can avoid it.  Lazy I guess.

---

### Post by Tanker Bob on 2010-01-23
Or you could try installing from the [Mozilla-Daily-Build PPA](https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa). Worked like a charm for me.

---

### Post by pqwoerituytrueiwoq on 2010-01-23
i believe it uses a different folder to store the setting home file [alt]+[h]
.mozilla-thunderbird and .thungerbird all you should have to do it rename the folder
i don't remember which is the right folder you want
edit:
skimmed 1st post
try copying the inner folder the blabla.default

---

### Post by caro on 2010-01-23
> **pqwoerituytrueiwoq said:**
> 
try copying the inner folder the blabla.default

i did that.  the first time i copied the entire contents of the profile folder (all files) and when i launched TB it said that another instance was running.  so i removed the copied contents and then just moved the contents of the profile's mail folder.  no luck.

---

### Post by Tanker Bob on 2010-01-23
> **caro said:**
> i did that.  the first time i copied the entire contents of the profile folder (all files) and when i launched TB it said that another instance was running.  so i removed the copied contents and then just moved the contents of the profile's mail folder.  no luck.

I'm guessing, but it doesn't look like you gave it an opportunity to import your stuff from scratch. Try uninstalling TB 3, delete the .thunderbird folder, leave your TB 2 folder intact, then reinstall TB 3. See if it imports TB 2 under that circumstance where there's no evidence of TB 3 ever having been there.

---

### Post by caro on 2010-01-23
> **Tanker Bob said:**
> I'm guessing, but it doesn't look like you gave it an opportunity to import your stuff from scratch. Try uninstalling TB 3, delete the .thunderbird folder, leave your TB 2 folder intact, then reinstall TB 3. See if it imports TB 2 under that circumstance where there's no evidence of TB 3 ever having been there.

Tried that too.  No go.

---

### Post by Tanker Bob on 2010-01-23
> **caro said:**
> Tried that too.  No go.

Hmmm. You've already tried everything I would have tried except one. Did you try using TB 3's [profile manager](http://www.mozilla.org/support/thunderbird/profile)?

---

### Post by caro on 2010-01-23
Well, I tried copying the TB2 profile to /.thunderbird again.  This time I edited profile.ini to point to the old profile that I moved.  It worked, but there are some files in the original profile that are not there in the one I moved.  Everything seems to work though so I guess it's all good.

---

### Post by Tanker Bob on 2010-01-23
> **caro said:**
> Well, I tried copying the TB2 profile to /.thunderbird again.  This time I edited profile.ini to point to the old profile that I moved.  It worked, but there are some files in the original profile that are not there in the one I moved.  Everything seems to work though so I guess it's all good.

Outstanding. Thanks for passing on the solution so that we can all learn.

---

### Post by caro on 2010-01-23
Thanks for your help.

---

### Post by partofthething on 2010-04-06
> i did that. the first time i copied the entire contents of the profile folder (all files) and when i launched TB it said that another instance was running. so i removed the copied contents and then just moved the contents of the profile's mail folder. no luck.Wait, I'm still having the problem where it says there's another instance running. How did you bypass that? So you moved rather than copied?

---

### Post by misterfixit on 2010-04-14
I did the profile thing and started TB3 .. it has been sitting there for the last 30+hours with a message at the bottom "Determining which messages to index".  OK, I know I had a lot of messages in the various IMAP and POP files, but 30+ hours???

---

### Post by misterfixit on 2010-04-14
> **misterfixit said:**
> I did the profile thing and started TB3 .. it has been sitting there for the last 30+hours with a message at the bottom "Determining which messages to index".  OK, I know I had a lot of messages in the various IMAP and POP files, but 30+ hours???

Still sitting there are some 45 hours.  Well, what do you know, looks like the "new and improved" Thunderbird is hosed.  This was a straight install along with the usual sudo aptitude upgrade stuff.  Well Surprise, Surprise as old Gomer Pyle would have said.

I am fortunate in that I run PINE alongside of the GUI  stuff, so I've not missed anything.

Oh and it is becomming pretty difficult to find the last version 2 of TB now ... Anyone have an ftp link to a ubuntu tb2 that I can leach?

---

