---
title: "best way to back up user account"
date: 2009-12-27
forum: General Help
---

### Post by MichaelBurns on 2009-12-27
What is the best way to back up a user account so that, if someone badly messes up their account, then I can just do a simple restore to the last known working backup?  Right now, I am just using the admin account to periodically make copies of everyone's home directories.  I have already had to restore using this implementation, and it is somewhat of a pain (chown and all that).  Is there a better way (i.e. a recommended or official way that I am supposed to do it)?

---

### Post by Barriehie on 2009-12-27
> **MichaelBurns said:**
> What is the best way to back up a user account so that, if someone badly messes up their account, then I can just do a simple restore to the last known working backup?  Right now, I am just using the admin account to periodically make copies of everyone's home directories.  I have already had to restore using this implementation, and it is somewhat of a pain (chown and all that).  Is there a better way (i.e. a recommended or official way that I am supposed to do it)?

I use tar, some will say rsync, 5 times a week to backup /etc, /www, and /home.  Just this AM I managed to rename EVERY file/folder in my home dir to a 10 character random name and that backup 2 hours prior saved my b***. :)

Barrie

---

### Post by amac777 on 2009-12-27
What is the command you are using from the admin account to make the copies? By using the correct command, you should be able to preserve all the ownership and permissions on the files so it would be painless to restore.

For example, to make a backup of a user called joe:

```
sudo rsync -a /home/joe /root/backups
```

That will put joe's user files in a backup directory off the root account while keeping all the ownership set to joe.

Then to restore you can follow these steps:

```
sudo mv /home/joe /home/joe-old
sudo rsync -a /root/backups/joe /home
```

Once you confirm everything is working as it should be and you don't need any of the files in joe-old, you can delete the old version of joe's folders:

```
sudo rm -r /home/joe-old
```

Hope this helps.

EDIT: the regular cp (copy) command has the -a parameter to maintain all the ownership and go recursively through the directory structure as well.

---

### Post by bodhi.zazen on 2009-12-27
It does not matter HOW you back up, just keep in mind you need to test your backup method to make sure you know how to restore from back up.

Many people forget this step and then do not know how to restore lost data or worse find out too late their backup strategy did not work.

---

### Post by lisati on 2009-12-27
> **bodhi.zazen said:**
> It does not matter HOW you back up, just keep in mind you need to test your backup method to make sure you know how to restore from back up.

Many people forget this step and then do not know how to restore lost data or worse find out too late their backup strategy did not work.

+1.

My biggest failings in this area are either forgetting what I called the backup folder or where I put it.

---

### Post by Barriehie on 2009-12-27
> **bodhi.zazen said:**
> It does not matter HOW you back up, just keep in mind you need to test your backup method to make sure you know how to restore from back up.

Many people forget this step and then do not know how to restore lost data or worse find out too late their backup strategy did not work.

+1, yep, looked right at it and said "Now what???..." :)

---

### Post by MichaelBurns on 2009-12-28
Thanks to all of you who replied; all quite helpful.  I was half in fear of calling down the wrath for pretending to be a computer admin when I am not, but anyway, it would only be forum wrath, so better to ask than not.

I was just using the cp command.  I forget the way that I did it the first time, but this time I have used, for example to backup the anyone account from pwd=/home/:
```

sudo mkdir anyone_20091227
sudo cp -a -r anyone/* anyone_20091227/.

```
So, now, in the /home/ directory, ls will show:
```

anyone   anyone_20091227

```
Now that I have taken the time to write out my steps, I see an immediate flaw:  the owner of the anyone_20091227/ is going to be the admin account user.  That's a simple fix, right?  I just do a chown on that folder?  Well, I'm away from that computer (my mom's computer) until the next visit, I have no idea when.  I'll try to remember to update this thread with any test results at that time.  I might then also try tar and rsync, and decide which method I like the best.

Thanks again to all of you!

---

### Post by amac777 on 2010-01-01
You do not need to create the dirctory, use chmod, or the -r option for copy. Just use this:

```
sudo cp -a anyone anyone_20091227
```

---

