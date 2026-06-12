---
title: "Startup Script"
date: 2010-12-14
forum: General Help
---

### Post by godslam on 2010-12-14
I've seen how to make scripts for startup, but I need something a bit more advanced.

I need a script to run at startup and do one thing then do the next thing after that is finished.

I'm not a Linux pro and I also can't do a test of this because it could mess up when I'm doing if it doesn't work.

I'm running a Minecraft server and it's being run from /dev/shm with hourly backups.

On startup, I need it to move the backup folder to /dev/shm (which is easy), but then I need it to run a file that's in /dev/shm/server when it's finished copying. I have a feeling this is easier than I'm making it out to be, but I'm posting here to make sure I have it all set up correctly first.
A timer isn't 100% reliable in this instance, so I need something better. Is there a way to tell when "rsync -au --delete /dev/shm/server/ /media/Julia/server" finishes running so I can access it and run a file?

Thanks.
~godslam

---

### Post by TeoBigusGeekus on 2010-12-15
Use && (and operator) between bash commands: only if the first command finishes successfully the second one is executed.

---

### Post by godslam on 2010-12-15
> **TeoBigusGeekus said:**
> Use && (and operator) between bash commands: only if the first command finishes successfully the second one is executed.

Thank you very much.
That is all I needed. =)

Just making sure though. If I do:

```

#!/bin/sh
rsync -au --delete /dev/shm/server/ /media/Julia/server
&&
java -Xms1024M -Xmx1024M -jar Minecraft_Mod.jar nogui

```

Will that work?
Or do I put:

```

#!/bin/sh
rsync -au --delete /dev/shm/server/ /media/Julia/server && java -Xms1024M -Xmx1024M -jar Minecraft_Mod.jar nogui

```

And that will wait until rsync finishes to run Minecraft_Mod.jar?

Thanks again. =)

---

### Post by TeoBigusGeekus on 2010-12-15
The second one just to be sure.
Not only will it wait for rsync, but if rsync fails for some reason, it won't go to the second command.

---

### Post by godslam on 2010-12-15
> **TeoBigusGeekus said:**
> The second one just to be sure.
Not only will it wait for rsync, but if rsync fails for some reason, it won't go to the second command.

Sweet. That should work flawlessly then.

Off-topic: Love your avatar.

I don't hate Windows as an OS that much, but I can't stand most of their proprietary stuff. =P

---

### Post by TeoBigusGeekus on 2010-12-16
> **godslam said:**
> Sweet. That should work flawlessly then.

Off-topic: Love your avatar.

I don't hate Windows as an OS that much, but I can't stand most of their proprietary stuff. =P

Thanks mate!

---

### Post by godslam on 2010-12-16
> **TeoBigusGeekus said:**
> Thanks mate!

I just realized that I may have an issue.

I use rsync in cron and I have the --delete option on it. Does that mean that if cron activates at the same time that it's gonna delete everything since the folder isn't there anymore?

In case you don't follow:

test.txt is on the ramdisk.
rsync copies it to the Desktop.
Restart and test.txt is gone.
On startup it's told to copy text.txt back to ramdisk.
Cron activates and tries to copy from ramdisk to Desktop and since file doesn't exist, deletes it from Desktop.


Is that something that I'll have to worry about? I'd remove the --delete option, but only if I truly have to.

---

### Post by Cheesehead on 2010-12-16
One easy method is a timestamp. One for the last restart, a second for the last succesful copy to ramdisk. A timestamp can be as simple as 'touch /tmp/mytimestamps/last_restart'

If the last_restart is newer than last_copy_to_ramdisk, then the copying from desktop needs to happen, and the reverse should not. If the last_restart is older than last_copy_to_ramdisk, then the rsync update from the desktop should be fine.



Another easy method is setting a flag. It's a lot like a timetamp, but even easier.
When the initial setup of the ramdisk is complete, create the flag: 'touch /tmp/myflags/ramdisk_setup'
Befor running rsync, simply check for the existence of the flag.


Another more complicated method is to use Upstart events. But taking the time to learn Upstart is a good thing, it comes in handy!
Have the cron job emit a signal like 'time-for-backup' instead of triggering rsync directly.
One the initial ramdisk setup is complete, emit a signal like 'ramdisk-up'
Have an Upstart conf file that triggers the rsync backup only when both signals are true. Upstart signals are not persistent across restarts, so the listener won't be fooled by an old signal.

---

