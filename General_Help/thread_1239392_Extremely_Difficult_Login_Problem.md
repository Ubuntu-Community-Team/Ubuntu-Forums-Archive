---
title: "Extremely Difficult Login Problem"
date: 2009-08-13
forum: General Help
---

### Post by lukeisthecoolest on 2009-08-13
I made a major mistake and need a genius mind to help pull me out of this ditch. So what happened was I tried to change my user's profile to be linked to the root folder but everything got messed up. Now everytime i try to login i get an error that says: "User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users"

If anyone could help me solve this disastorous problem it would be greatly appreciated.

---

### Post by SPr on 2009-08-13
[http://ubuntuforums.org/search.php?searchid=62922693](http://ubuntuforums.org/search.php?searchid=62922693)

[http://ubuntuforums.org/showpost.php?p=7753382&postcount=3](http://ubuntuforums.org/showpost.php?p=7753382&postcount=3) for other links; taken from this thread: [http://ubuntuforums.org/showthread.php?t=1234865&highlight=User%27s+%24HOME%2F.dmrc+file](http://ubuntuforums.org/showthread.php?t=1234865&highlight=User%27s+%24HOME%2F.dmrc+file)

---

### Post by zkriesse on 2009-08-13
If you still have a live cd you could try the repair system option.:popcorn:

---

### Post by tgeer43 on 2009-08-13
Not really that difficult of a problem. Try the following:

Boot into recovery mode from the grub menu and then select the root shell. Now enter the following commands replacing 'tgeer' with your own user name:
```
chmod 644 /home/tgeer/.dmrc
chown tgeer /home/tgeer/.dmrc
chmod -R 700 /home/tgeer
chown -R tgeer /home/tgeer

shutdown -r now
```That ***should*** put you back right.

tgeer

---

### Post by lukeisthecoolest on 2009-08-18
> **tgeer43 said:**
> Not really that difficult of a problem. Try the following:

Boot into recovery mode from the grub menu and then select the root shell. Now enter the following commands replacing 'tgeer' with your own user name:
```
chmod 644 /home/tgeer/.dmrc
chown tgeer /home/tgeer/.dmrc
chmod -R 700 /home/tgeer
chown -R tgeer /home/tgeer

shutdown -r now
```That ***should*** put you back right.

tgeer

how do i select the root shell?

and where is the repair system option on the live cd?

---

### Post by tgeer43 on 2009-08-20
Sorry for the delay. I just suffered a massive HD failure and spent a ton of time trying to recover it before biting the bullet for a new drive. Thank God for regular backups!

I wasn't talking about doing it from the Live CD. Boot your regular HD install and on the Grub menu arrow down to recovery mode and on the next screen select the root shell or root shell with networking.

You *could* do it from the Live CD as well. You'd just boot it normally and then open up a terminal. Make sure the drive is mounted and change the path in each command to reflect the correct location where your drive is mounted.

For example, instead of:
```
chmod 644 /home/tgeer/.dmrc
```You'd put something like:
```
chmod 644 /media/disk/home/tgeer/.dmrc
```Just look in the /media directory (of the Live CD filesystem) to see the name of the folder that your drive is mounted to.

Probably best to do it from recovery mode on the HD install, though to avoid any confusion.

Hope this helps,

tgeer

---

