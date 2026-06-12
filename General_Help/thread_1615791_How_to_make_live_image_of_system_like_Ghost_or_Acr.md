---
title: "How to make live image of system like Ghost or Acronis?"
date: 2010-11-07
forum: General Help
---

### Post by ingramproductions on 2010-11-07
Does anybody know of a program that can make make images of the entire hard drive while it's in use? Like Ghost and Acronis can do?

I have a production ubuntu system that I need backups of, however, I can't power it off. Any ideas?

---

### Post by dino99 on 2010-11-07
clonezilla do the job

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by CharlesA on 2010-11-07
You want to image a machine while it's in use?

That would be a bad idea tbh, especually since files can change in the process of imaging. As far as I know Ghost and Clonezilla needs the machine to be powered off to do the imaging.

If you need backups while the system is up and running, I'd suggest looking into tar or rsync.

---

### Post by Mark Phelps on 2010-11-07
> **ingramproductions said:**
> Does anybody know of a program that can make make images of the entire hard drive while it's in use? ...

THAT's a problem.  Linux utilities won't allow you to do anything to a partition that is mounted; thus, you have to run partition backups when NOT running Ubuntu.

If you go to the Clonezilla site, they have directions for how you can add an entry to your GRUB2 script to be able to boot into Clonezilla and run it from your hard drive -- but there's no way you can run it from inside Ubuntu and backup a partition that's currently in use.

---

### Post by warfacegod on 2010-11-07
What about Remastersys?

---

### Post by ingramproductions on 2010-11-07
I use Acronis to make backups of the entire drive while the system is powered on. Acronis is installed on the system and we schedule weekly backups. You can't Do anything to windows partions while they're mounted either, but acronis takes a snapshot of the drive somehow, and it works great. Ghost does the same thing. There is a Linux version of acronis that will make full images of the drive while the os is running, however, I am looking for a open source or free tool to do this. Can tar or rsync do it?

---

### Post by CharlesA on 2010-11-07
It gets complicated if you do it when the system is running.

If Acronis works for you, why not keep using it?

---

### Post by ingramproductions on 2010-11-07
I use Acronis for Windows servers. I do not want to buy the linux version. I thought there would be an opensource tool that can do the same thing, but apparently, linux is lacking in this area.

---

### Post by ingramproductions on 2011-07-24
Results:

**Backing up Windows Servers**: Normal production servers, people don't shut them down to make full system backups (The entire OS and all partitions). They schedule full systems backups while the server is running, and they work fantastic, even when running exchange, sql, AD, or whatever...

**Backing up Linux Servers**: Normal production servers, you must physically shut the server off and perform an offline backup, wait for it to finish, then turn it back on (for a full system backup). Online full system backups do not exist in the Linux world, with the exception of Acronis for Linux [http://www.acronis.com/backup-recovery/server-linux/?source=us_googleABRSL_b&ad=abrsl&c=6668255897&k=acronis%20for%20linux&gclid=CMb4t4eWmaoCFQvKKgod3WAzwg]("http://www.acronis.com/backup-recovery/server-linux/?source=us_googleABRSL_b&ad=abrsl&c=6668255897&k=acronis%20for%20linux&gclid=CMb4t4eWmaoCFQvKKgod3WAzwg") (currently $835.00)

This is unfortunate for Linux administrators.

+1 Windows
-1 Linux

:(

---

