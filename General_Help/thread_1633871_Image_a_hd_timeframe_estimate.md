---
title: "Image a hd timeframe estimate"
date: 2010-11-29
forum: General Help
---

### Post by COKEDUDE on 2010-11-29
Can someone that has imaged a hd before give me a estimate of how long it will take to image a 200 gb ntfs hd. Would it take like an hour, 6 hours, a day, or several days? I'm trying to decide when and how to do it. Whether I leave my computer running overnight to do this, or use a old computer to do this. I don't wanna have my regular work computer tied up for several days.

---

### Post by howefield on 2010-11-29
For me, a 500 gig hard drive with an Ubuntu install on it, 3 partitions (ext4) but no personal data takes about 8 minutes to image with Clonezilla.

I guess it depends on how fast your computer is and how much data is being backed up, but in any event you shouldn't need to be worrying about tying up your computer for days :)

---

### Post by CharlesA on 2010-11-29
Depends on how much data you have and what method you are using to image it.

Using dd will take longer then using something like Clonezilla.

---

### Post by COKEDUDE on 2010-11-29
Sorry I forgot to say it is a 200 ntfs gb hd.

---

### Post by CharlesA on 2010-11-29
clonezilla should work fine with it, even if it'll take a while, since it has to save a load of data.

I'd say give it a few hours.

---

### Post by howefield on 2010-11-29
Again, it depends on how much of your 200gb disk is filled with data, good image creators such as Clonezilla will only back up the used sectors, in my experience with Clonezilla, it is a little slower with NTFS than with ext file systems but I'd be disappointed if it took much more than half an hour.

---

### Post by CharlesA on 2010-11-29
> **howefield said:**
> Again, it depends on how much of your 200gb disk is filled with data, good image creators such as Clonezilla will only back up the used sectors, in my experience with Clonezilla, it is a little slower with NTFS than with ext file systems but I'd be disappointed if it took much more than half an hour.
I've had clonezilla take about 30 minutes to clone 40GB of data from an NTFS drive.

---

### Post by COKEDUDE on 2010-11-29
> **howefield said:**
> Again, it depends on how much of your 200gb disk is filled with data, good image creators such as Clonezilla will only back up the used sectors, in my experience with Clonezilla, it is a little slower with NTFS than with ext file systems but I'd be disappointed if it took much more than half an hour.

It has about 160 gb of data. Will clonezilla have problems seeing the data if the hd has some problems? I haven't found any software except for testdisk that can see my data.

---

### Post by CharlesA on 2010-11-29
> **COKEDUDE said:**
> It has about 160 gb of data. Will clonezilla have problems seeing the data if the hd has some problems? I haven't found any software except for testdisk that can see my data.

If the hard drive is having problems, then it's unlikely you'll be able to recover much.

Try ddrescue.

---

### Post by COKEDUDE on 2010-11-29
> **CharlesA said:**
> If the hard drive is having problems, then it's unlikely you'll be able to recover much.

Try ddrescue.

I have been able to recover most of my videos and most of games and game related information with testdisk. The problem lies in small important files. I am having trouble recovering my small files like important word documents, important pdf's, important presentations, and several other small files.

---

### Post by CharlesA on 2010-11-30
> **COKEDUDE said:**
> I have been able to recover most of my videos and most of games and game related information with testdisk. The problem lies in small important files. I am having trouble recovering my small files like important word documents, important pdf's, important presentations, and several other small files.

If they are really important and you don't have backups, it might be worthwhile to look into some kind of data recovery service.

---

### Post by COKEDUDE on 2010-11-30
> **CharlesA said:**
> If they are really important and you don't have backups, it might be worthwhile to look into some kind of data recovery service.

My original got stolen thx to a careless data recovery service employee and my backup is my lovely messed up hd. I have had and heard of many bad experience's with data recovery service's so I really don't wanna waist my time or money with them again.

---

### Post by CharlesA on 2010-11-30
> **COKEDUDE said:**
> My original got stolen thx to a careless data recovery service employee and my backup is my lovely messed up hd. I have had and heard of many bad experience's with data recovery service's so I really don't wanna waist my time or money with them again.
I see. Check out [ddrescue]("http://www.gnu.org/software/ddrescue/ddrescue.html") for trying to recover data thru the read errors.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

