---
title: "How to set up Home file and backup server from an old computer."
date: 2010-12-08
forum: General Help
---

### Post by Nagrom_17 on 2010-12-08
Through the Black Friday shuffle of getting new hardware, I now have a 500TB external drive, a 1TB external drive, and an old computer I want to set up as a home server.
My family has a lot of photos that are currently stored on many different computers and are not backed up, I want 500gb of space for photos, and for those photos to be backed up. That would leave the other half of the 1TB drive for assorted things like personal backups, and general file storage.
I know enough how to set up Ubuntu server edition on the computer, but the options on how I can set up the storage is stumping me.


To Recap, I have 1.5TB of storage total split 1TB/500GB. I want 500GB to be used for a central storage for the 10+ computers in my house(mostly using Windows) and that 500GB would be automatically backed up. The 500GB that's left would be used for non critical files, and wouldn't be backed up.

Questions,
What is the best way of backing up the files? (script once a day that copies files? Some backup program?)

Would the 500gb drive be best for backing up to(having the 1TB be where people would put the pictures) or the other way around? Does it really matter?

Any tips on the cleanest way to have this work cleanly with Windows, Linux, and Mac? How well do photo programs(Picasa, Shotwell, iPhoto) like a setup like this? Is it possible to have different programs on different machines all reference the same file system without their automatic sorting(to folders, usually by date) messing each other up?

Thanks for any help you can give, I hope to be setting this up later today.

---

### Post by nothingspecial on 2010-12-08
Yes, this is all possible. I haven`t a lot of time right now but have a look at

rsync
cron
sshfs
ssh
samba

cheers

---

