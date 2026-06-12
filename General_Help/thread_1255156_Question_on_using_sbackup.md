---
title: "Question on using sbackup"
date: 2009-09-01
forum: General Help
---

### Post by CaesarLike on 2009-09-01
Hi there,

I have a few questions on how I would use sbackup in the event I had to reinstall Ubuntu.

Okay lets say I make a backup using the default settings for sbackup.
Does the backup include applications I have downloaded?  I assume it does not.

So in the event of needing to reinstall the OS am I correct in thinking that I would have to reinstall my applications before restoring from the backup?

Is it possible with sbackup to create a backup that would effectively return my OS to fairly much the way it was after doing an OS reinstall?  Or is sbackup basically an application to backup a users non system related files like music & documents etc?

---

### Post by infinitejones on 2009-09-01
> **CaesarLike said:**
> Or is sbackup basically an application to backup a users non system related files like music & documents etc?

Spot on. Sbackup is just designed to back up files (eg. your home directory), not to create an re-install image. 

(On that subject, I saw another thread on here a couple of mins ago asking if there's a Linux equivalent to Norton Ghost - I didn't read it but why not search for it, it might provide a solution for you.)

Anyway - if you let sbackup back up your complete home folder, then most of your application settings will be backed up too. That's because usually (by no means all the time, but usually) applications store their settings data in a hidden folder in the home folder (for example '.rhythmbox'). Hit ctrl-H in your home folder and you'll see them all.

So if you restore from an sbackup backup after a re-install, then re-install all your applications, the settings should be restored too. (I say should, because it depends on the application. If the re-installed version of the application is newer compared to the one before the re-install, there's a chance it won't be exactly the same.)

---

### Post by CaesarLike on 2009-09-01
Thanks infinitejones, I thought it would be something like that.  I am not really after creating the whole norton ghost restore image type thing for using linux, I have no issues with reinstalling the OS and the apps.  Synaptic makes this a breeze compared to using windows.  God the last time I did that with XP I litterally spent 2 whole days.  Wth Ubuntu it takes like 2 hours max, and that includes the reinstall update as well.
What I wanted to know was to what extent sbackup saved my files.  Saving my user files and many of the application data files is plenty for me as most of the linux apps I use dont really require too much in the way of user settings data.  And as for user files, thats what a separate storage partition is for. :)

---

