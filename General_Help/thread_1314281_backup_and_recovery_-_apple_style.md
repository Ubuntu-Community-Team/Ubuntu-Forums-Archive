---
title: "backup and recovery - apple style"
date: 2009-11-04
forum: General Help
---

### Post by caue.rego on 2009-11-04
*I really do need to choose better keywords for this topic, but until then let's call this "backup and recovery".*

_[FONT="Arial Black"]"Little" Introduction[/FONT]_
There are too many ways to backup Ubuntu and I need just one!

First I must say I'm a huge fan of Apple's Time Machine and that's the solution I would like to find for my Ubuntu. Hard Drives are fcking big enough to even hold Time Machine on themselves and I'm willing to lose half of it just to keep it safe. In fact, it's what I do in my OSX86.

So I want to organize here the options we currently have to backup ubuntu. I've tried many methods for backing up ubuntu, and I'm still trying few more. It's hard for me to try because I can't stop everything else and simulate recoveries. Even if I could, it would be just a simulation. I rather have data from people who actually experienced a needed situation.

I don't want or like to use solutions like mirroring a disk image, using thousands of CDs, and make too much redundant garbage out of the system, although I feel obligated to use them sometimes because the other options doesn't give good recovery or sometimes no recovery at all! It's almos like just building a list of what I had so I can re-install and re-configure all over again.

So, please, if you don't know deep enough about Time Machine and have never have seem or experienced something similar, don't bother posting anything here. I'll give some heads on how amazing apple did that solution, and oddly how simple it is.

I hope someone will be able to just copy it and make it better (a.k.a. highly customizable) in Ubuntu! With Time Machine you can't, for example, backup to more than one device simultaneously. Nor use a remote device (as far as I know).

In the middle of writing this I almost gave up because I found [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem) but then I realized it just gives yet more options (a lot of which I've tried or read about), rather than diminishing it. My purpose here is to find just one, the one closer to "apple style".

_[FONT="Arial Black"]Apple Style[/FONT]_
Time Machine.

Take away the beauty of it and the fuzz, and what's left? A very reliable solution using not just software but cheap hardware as well. Well, if you don't go by with a Time Capsule, of course.

It's meant to be used with a secondary harddrive, but could be as well just one disk with a same-sized or bigger partition for the backup. It just won't magically recover data if the hardware goes bad, of course.

It's a simple schedule process that builds directory structured by date and time (though a rdiff rsync) which you can easily navigate through using any given method. Hourly it will make backups of your whole system, including file systems. But just once, and just the ones that matter for recovery. Specially configuration files. Every other file backed up which wasn't changed since last backup is just a symlink. Well worth the size for the convenience of also being able to restore any given whole backup point or even single files from them.

You can fine tune few configurations, but not much like you'd be able to do on Ubuntu or most *nix systems. So you wouldn't be able to use it to backup just images for example - although there's a whole philosophy behind it since we don't need to do that for images, just use iPhoto instead (or Picasa).

And, granted, if you COMPLETELY LOSE YOUR COMPUTER, but your hard disk with a Time Machine backup is fine, you can BUY A NEW COMPUTER and you won't have lost a thing. Well, maybe few things, but not much since it does, as it announces, hourly backups for past 24h, daily backups for the past month and weekly backups until it gets full. Older backups are naturally removed to give room for new ones.

It is the ultimate easiest backup solution, but even then it's not best for all situations. It's still a good idea to make backups to DVDs and CDs with just relevant data and no system files once in a while. And it's also a great idea to have a custom system disc for installing a fresh new OS whenever is needed, or as a recovery tool (love Super OS and Ubuntu Install disk).


_[FONT="Arial Black"]Current Options[/FONT]_
As I said, there are too many, and this is already cut off!

- [_back in time_]("http://backintime.le-web.org/")
This is great, and it's what I'm currently using. It feels like Time Machine. But I never tried a recovery and it doesn't seem like it could do the job too well. Please, anyone who have experienced this, give us some input! I've tried [_TimeVault_]("https://wiki.ubuntu.com/TimeVault") and [_FlyBack_]("http://flyback-project.org/"), both of which also try to copy Time Machine, but backintime seemed to work better to me.

- [_remastersys_]("http://www.remastersys.klikit-linux.com/ubuntu.html")
This seems like a mix of partimage with pybackpack (due to the friendly interface). But I couldn't even finish a single backup. I left it overnight and today it said ISO file was too big. It's not compling with the first half of the topic at all, but it would be nice having such an easy solution for eventually making a backup of the whole system as an image AND/OR the system installation as fresh new custom made. So, this is a very good suggested solution for backup and recovery which I will try a little more.

- [_pybackpack_]("http://www.ubuntugeek.com/pybackpack-a-user-friendly-file-backup-tool-for-ubuntu-linux-desktop.html")
Never tried this one, but seems quite friendly and new. Sure will give it a shot as it seems like it does samething as partimage, but friendly.

- [_FS archiver_]("http://www.fsarchiver.org/Main_Page")
Haven't tried it, it's probably my next attempt. Any inputs here? This seems like a nice new idea, if it's a file system for backups. I'm already expecting it to be a whole incomplete backup solution, tho.

_[FONT="Arial Black"]Current Non-Options[/FONT]_
Those are backup options, but not quite for easy recovery as the suggested topic!

- [_partimage_]("http://ubuntuforums.org/showthread.php?t=287522")
This is so far the best way to be able to recover a system from any crash. But it's also the worst possible way to do the backup (quite a harassment) and it has almost no optimization for storing data, thus wasting a lot of space that could be used for better backup, with relevant data. It's all command-line and not friendly at all, even if it's not "that hard".

- [_Clonezilla_]("http://clonezilla.org/")
I won't even cite Norton Ghost since this is the Ubuntu way. Haven't tried this option because it's way far from what I need, but this is probably the most straight forward to backup and, above all, easily restore from removable solid media such as DVD, pen drives or even external HD. This is made to CLONE rather than backup, although it can be used for such with ease.

- [_sbackup_]("https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite") "Simple Backup Suite"
I could only find two options in Add/Remove on 9.04 Jaunty, this is one. sbackup is more complete, and it will create packed files in /var/backup as default, which is kinda nice. But none seemed to do the whole "backup and recovery" job very well. sbackup is actually hard to configure and by default won't backup any file larger than 10Mb, for example. Its purpose seem to be keeping an *almost* random backup which would be used to recover the system if anything crashes (say kernel) while maintaining the backup size very small with relevant data and not much more. It's a nice concept, but it bloats a lot of backup and it will not leave any kb free for your system soon enough, becoming a trouble.

- [_Keep_]("http://jr.falleri.free.fr/keep")
Keep is basically just a little GUI for rsync and cron. This was the only other option I found on Add/Remove and it is fairly as simple as I wished a solution should be - at first. But it's way too incomplete. I don't even consider using this as an option, but some people may find it useful since it is highly customizable (I guess). It comes with no suggested configuration whatsoever.

- [_Amanda_]("http://www.zmanda.com/amanda_advantage.html")
Never heard of any of those till today. But this looks like cloud, and when I think of that I think [_dropbox_]("http://getdropbox.com"). It clearly isn't the same thing, although it does use Amazon, but I wonder if the server is needed, if this is the only way it works, and how good of a "backup and recovery" solution this is. I guess this, just as dropbox, is more like to do "selective backup" and no recovery at all. Clouding is great for relevant data, and it have to be mostly manually selective. This is a perfect example of what I **don't** want to discuss in this topic.

---

