---
title: "Backup"
date: 2010-07-02
forum: General Help
---

### Post by jereece on 2010-07-02
I am looking for recommendations for a backup program.  I want something simple, will run automatic on time (e.g. daily, weekly, etc.) and manual.  Something that I can predefine folders to back up and the location to backup to (e.g. external hard drive).  When I search Software Center I find a lot of things.  What are your recommendations?

---

### Post by mike555 on 2010-07-02
for simple backups I use " LuckyBackup" , you set it up and it just works ........... if you need more look into " Back in Time" ...

---

### Post by nmaster on 2010-07-02
here is a little guide on LuckyBackup:[http://www.linux.com/learn/tutorials/322632-easy-linux-backup-with-lucky-backup](http://www.linux.com/learn/tutorials/322632-easy-linux-backup-with-lucky-backup)

i like using fsarchiver so that I can back up the entire OS (not just me personal files).  it has a lot of nice features and it gets good reviews: [http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)

---

### Post by Pepse3 on 2010-07-04
I, too, would like to backup my complete Linux HDD but I am running KUBUNTU 8.04.  Luckybackup only goes back to 9.10.  I want a complete backup to DVD.  Any ideas?

---

### Post by sgosnell on 2010-07-04
Probably the easiest is remastersys.  It will back up to just about anything.  If you want to do scheduled automated backups, rsync through a cron job is probably the best way to do it.

---

### Post by Pepse3 on 2010-07-05
It looks like a good thing but I think I have a problem.  I have 4 HDD's, HDD1=KUBUNTU 8.04, HDD2=(was)win7rc1, HDD3=Mandriva 2010.0, and HDD4=winXP.  My GRUB bootloader is through Mandriva, and from what I could tell that might be a problem for me.  

Pepse.

---

### Post by CharlesA on 2010-07-05
I use an rsync script in a cronjob for daily backups. :-)

---

### Post by sgosnell on 2010-07-05
That's going to be a lot of backup, and might take awhile.  Rsync, automated to run during the night as a cron job, might be the best route.  You could schedule a different HDD each night, if that's often enough.  If you need a nightly backup of each, it can be done, but it won't be instantaneous.  If you just need one backup of each, look at grsync.  It's a GUI frontend for rsync, and doesn't take as much knowledge of rsync options, because you can make the selections in the GUI.  It's not easy to automate, though.  Remastersys can do a separate backup of each HDD easily enough, but do you have the storage space for all that?

---

### Post by Pepse3 on 2010-07-09
I guess I didn't explain it right.  My point is that I have 4 HDD's.  I only want to backup the Kubuntu 8.04 HDD.  I stated I might have a problem because of my bootloader (GRUB) is set to look at Kubuntu but it is the (better) Mandriva GRUB bootloader so that is why I stated that it might be a problem.  

  Also, I am trying to backup to a DVD because at this time I can not afford an extra hard drive.  If we get something that will backup to a DVD I have some double layer DVD's if needed.

Pepse.

---

### Post by sgosnell on 2010-07-09
Rsync will back up to your DVD drive, as will remastersys.  If grub isn't right on the Kubuntu drive, you can always reload it after you restore the backup.  Always keep a liveCD of Ubuntu on hand for booting in case of a HDD problem, and you can make repairs from it easily enough.

---

### Post by HermanAB on 2010-07-09
The reason there aren't any good backup programs, is because these programs are usually written by new users and end up being overly complicated.  Old-timers simply use a one line rsync Bash script in /etc/cron.daily.

Have a look a Dervish.  It is one of the better overly complicated backup programs.

---

