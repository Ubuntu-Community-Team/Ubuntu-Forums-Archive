---
title: "newbie questions"
date: 2011-04-10
forum: General Help
---

### Post by TuxSam on 2011-04-10
[INDENT]I am a newbie so let me say it before i get in trouble :)[/INDENT]

I have searched here and google for the sloution to most of these issues. I probably found the answers but didn't realise...

please help me repost in a more appropriate thread if applicable.

a. at some point ubuntu started asking for my login password to unlock my loginkeyring. i would like it to just ask me for it when it is needed not whenever i login.

b. it does login without the password it just has a prompt for it. the issue here is that if i am away at bootup the screensaver will go on but will not lock if it was not supplied with the login password. is that a bug?

c. headphones dont work. no sound, and speakers still speak. ( ifound this bug in a lot of places going far back but cannot understand if/what is the fix)

d. Cannot reserve MMIO region (also well documented, my fault that i don't understand if I can do anything to fix it)

e. when i plug in my phone to use it as a mobile broadband connection it takes a while until it is recognized. (it shows up in dmesg)

f. this might not belong here but i don't know a better place.
I boot from a portable hard drive and the ubuntu partition is not too big. I use an external hardrive at home that is big enough. what would i do to mirror the installation to the external harddrive (so that updates and OS changes get saved and i can boot from the unportable external if needed) and move all but the most recent files from the /home dir to a mirror of it on the external. I want to end up having the OS installation with just the most recent user created files on my laptop and the full set of files (pictures videos mp3 all other saved and downloaded files) on a backup external harddrive.

---

### Post by profeta81 on 2011-04-11
> **TuxSam said:**
> [INDENT]I am a newbie so let me say it before i get in trouble :)[/INDENT]

I have searched here and google for the sloution to most of these issues. I probably found the answers but didn't realise... please help me repost in a more appropriate thread if applicable.

Hi... these seem beginner questions... next time post them there...

> a. at some point ubuntu started asking for my login password to unlock my loginkeyring. i would like it to just ask me for it when it is needed not whenever i login.

loginkeyring? you mean that once you turned on your pc, it asks you to login and you'd prefer it to login automatically instead? if that's the case, you can do

System -> Administration -> Login Screen

once the dialog opens unlock it, and then select the option "Login as ... automatically"

> b. it does login without the password it just has a prompt for it. the issue here is that if i am away at bootup the screensaver will go on but will not lock if it was not supplied with the login password. is that a bug?

If you're not logged on, then the screen doesn't need to lock, that's not a bug, that's just the way it works. The locking of the screen is generally used in places where PCs are shared between many users to prevent people gaining access to somebody else's account. If you don't want your screen to lock when the screen saver starts (after you've logged on and regardless of whether you had to type the password to log or the login was automatic) then do:

System -> Preferences -> Screensaver

and deselect "Lock screen when scrensaver is active"

> c. headphones dont work. no sound, and speakers still speak. ( ifound this bug in a lot of places going far back but cannot understand if/what is the fix)

are you sure the headphones plugged and volume not at minimum??

> d. Cannot reserve MMIO region (also well documented, my fault that i don't understand if I can do anything to fix it)
Sorry, no idea what the problem may be here. Please try to be a bit more specific...
> e. when i plug in my phone to use it as a mobile broadband connection it takes a while until it is recognized. (it shows up in dmesg
is this a problem? how long you have to wait? again, please try and be a bit more specific
> f. this might not belong here but i don't know a better place.
I boot from a portable hard drive and the ubuntu partition is not too big. I use an external hardrive at home that is big enough. what would i do to mirror the installation to the external harddrive (so that updates and OS changes get saved and i can boot from the unportable external if needed) and move all but the most recent files from the /home dir to a mirror of it on the external. I want to end up having the OS installation with just the most recent user created files on my laptop and the full set of files (pictures videos mp3 all other saved and downloaded files) on a backup external harddrive.
If you want to be able to boot from the "non-portable" external hard drive, then you may just proceed to a fresh install specifying a partition on the external as your / directory. As for "mirroring" files, that's usually called backing up and you have various methods to do that. You can take a look at this [BackupYourSystem]("https://help.ubuntu.com/community/BackupYourSystem"); I personally use rsync for my own backups.

one list of commands that may work for you are these: say your large home is in /media/disk/large_home and your small home directory is in /home/small_home and you want to synchronize all your files to the large home first, and then delete the ones which are older than 6 days
```

LHOME=/media/disk/large_home/
SHOME=/home/small_home/
DAYS=6
rsync -vau $SHOME $LHOME
find $LHOME -mtime +$DAYS -exec rm {} \;

```
the first three lines only create some variables (you should edit these to fit your needs), the line beginning with rsync synchronize all the files from the small home to the large one; the last line finds all files older than 6 days and deletes them. you can create a small scripts with these lines if you want... be careful though not to delete important files or to update a file in the large home which was separately edited.

hope this was helpful
cheers ;)

---

### Post by jmszr on 2011-04-11
TuxSam,

The "cannot reserve MMIO region" is a message, not an error: [http://ubuntuforums.org/showthread.php?t=1478677](http://ubuntuforums.org/showthread.php?t=1478677) .

This helps explain: [http://lwn.net/Articles/270939/](http://lwn.net/Articles/270939/) .

---

