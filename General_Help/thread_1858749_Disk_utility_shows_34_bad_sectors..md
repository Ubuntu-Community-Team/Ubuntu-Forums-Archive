---
title: "Disk utility shows 34 bad sectors."
date: 2011-10-12
forum: General Help
---

### Post by pretty_whistle on 2011-10-12
I used Ubuntu's disk utility and it says there are 34 bad sectors.  Then I tried what I found here for using fsck to fix it:

[http://justcheckingonall.wordpress.com/2010/07/18/howto-repair-broken-ext4-partitions/](http://justcheckingonall.wordpress.com/2010/07/18/howto-repair-broken-ext4-partitions/)

I still have the 34 bad sectors.  What does this mean and what can I do?

Here's the screenshot btw:

[IMG]http://i53.tinypic.com/5fi6pc.png[/IMG]

---

### Post by pretty_whistle on 2011-10-13
Nevermind.  I figured it out.

Wished I could delete an unecessary thread at a time like this.

---

### Post by 3rdalbum on 2011-10-13
You can't "fix" bad sectors. The advice you linked to is only for a corrupted partition, not for physically bad sectors.

If you've got 34 bad sectors, then the disk is definitely failing. Get all the data from it straight away and replace it. You have probably already lost data. The longer you wait, the more data you will lose.

---

### Post by pretty_whistle on 2011-10-13
This explanation here is interesting :

[http://www.easeus.com/resource/bad-sector.htm]("http://www.easeus.com/resource/bad-sector.htm")

This may be normal wear and tear and therefore nothing to be concerned about or it may have come from the manufacturer that way.

Considering that I'll simply keep an eye on it.

---

### Post by thatguruguy on 2011-10-13
You apparently are ignoring the part where it says:
> If your hard drive develops a bad sector, back the hard drive up  immediately. If the bad sector was caused by a faulty drive head, the  problem can quickly spread to other sectors on the disk.

---

### Post by pretty_whistle on 2011-10-13
> **3rdalbum said:**
> You can't "fix" bad sectors. The advice you linked to is only for a corrupted partition, not for physically bad sectors.

If you've got 34 bad sectors, then the disk is definitely failing. Get all the data from it straight away and replace it. You have probably already lost data. The longer you wait, the more data you will lose.
What exactly does it mean when you said, "You have probably already lost data. The longer you wait, the more data you will lose." ?  What data?

---

### Post by pretty_whistle on 2011-10-13
> **thatguruguy said:**
> You apparently are ignoring the part where it says:

Actually no.  It says it can quickly spread if this is the cause, so that's what I'm keeping an eye on-to see if it'll quickly spread or not.

My laptop is 3 years old... so..... it may be replacement time soon.  I'll wait and see what happens. (I have a backup, as I usually have, so I'm ready if it pops soon.)

---

### Post by pretty_whistle on 2011-10-13
What are the symptoms of hard drive failure, besides these:


> 
'Blue screen of death': 
Have you ever been working on your PC or laptop and then suddenly a blue screen with a lot of information written on it appears? Well, that is a sign of hard disk failure. That blue screen is what the IT specialists call the 'blue screen of death'. As the name suggests, it means that something is dying, which in this case is the hard disk. It may also appear when your computer is booting. This blue screen appears because there exists some corrupted sectors on the hard drive and the system is unable to read the sectors.

Continuous rebooting of computer: 
Sometimes when booting your computer, it tends to reach a certain point in the boot process and then it automatically reboots. This is a sign that the hard drive is failing due to presence of viruses. There are certain viruses that infect the boot sectors of the hard drive and corrupt them in such a way that it makes the boot files form a continuous loop. This is why the computer will keep rebooting.

Error messages: 
You could be working on your computer and receive error messages such as 'Hard Drive Failure', 'Hard Drive not found', 'Operating system missing' or any other error that is related to the mentioned ones. If such errors keep popping up, it means that the computer drive is failing. This, again, is due to corruption of information stored on it. Being unable to interpret the said information, the system gives the error messages.

System freezing and hanging: 
This is one of the most common ways that signify hard drive failure. As you may have noted, most of these signs of hard disk failure are because of corruption of information on the drive. The system freezes or hangs because it is unable to access the necessary files for processing certain instructions because of...you guessed it...corruption of information on the hard disk.

Excessive overheating of your drive is a sign of worn out parts and damaged components.

Funny sounds like clicking and vibrating are as a result of mechanical problems. If you happen to notice any of these signs it would be right time to perform a back up.

Any others?

---

### Post by WasMeHere on 2011-10-13
New bad sectors are definitely a sign of a failing disk.

A new disk may have a few bad sectors, and it may run for years without any new bad sectors. But when bad sectors appear on an aging disk, clone it, or at least, backup your personal data!

---

### Post by pretty_whistle on 2011-10-13
> **Olle Wiklund said:**
> New bad sectors are definitely a sign of a failing disk.

A new disk may have a few bad sectors, and it may run for years without any new bad sectors. But when bad sectors appear on an aging disk, clone it, or at least, backup your personal data!

Ah.  I'll make a note of that.

I always have backups so I'm good to go on that one.

---

