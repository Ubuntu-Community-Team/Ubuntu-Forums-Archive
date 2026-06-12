---
title: "Deja Dup seems ridiculously slow"
date: 2010-09-10
forum: General Help
---

### Post by Dave M G on 2010-09-10
My goal is to make an encrypted back up to a remote server by FTP using Deja Dup.

The interface is really clean and easy to use, so the set up and connection was great.

I do have a lot of data to back up. It's my entire /home directory, which comes in at about 350 GB.

Using "Back In Time", doing the back up for the first time took a few hours. However, "Back in Time" has no encryption option, so it's not the preferred back up solution.

Using Deja Dup, with encryption on, the back up, so far as I can tell, has not yet made a complete initial back up, and it has been running for about 6 days. Sometimes it dies with various errors, such as a dropped connection. But I've been more or less running it continually.

Isn't that very slow, even with encryption turned on?

I'd like to get to a point to where I can verify that I've made a full and complete backup, and then from that point make incremental back ups daily.

What should I expect out of Deja Dup for speed? How can I verify that it has made a complete backup?

By the way, I'm on a 1Gb optic connection, and given the speeds of all my other internet activities, I don't think there is anything throttling the upload speed outside of Deja Dup.

Any advice or tips would be much appreciated.

---

### Post by Dave M G on 2010-10-11
Since posting the first message in this thread, I've upgraded to 10.10.

I had hoped that maybe Deja Dup would have improved slightly, but it has not.

As of this writing, in the weeks I've been trying Deja Dup, it has not once yet successfully made a complete backup.

It always gets about two thirds of the way through, and dies with vague errors about being unable to copy the files, for any one of a number of reasons such as a network error or mistake in the encryption.

For example:
```
BackendException: Could not copy /tmp/duplicity-Xb9LSE-tempdir/mktemp-sVZPcP-5 to ftp://xxxxxxxx@xxxxxxxxx.com/duplicity-full.20100901T150541Z.vol9999.difftar.gpg
```

So, basically, Deja Dup kind of sucks.

Is there a way to get it to complete its backups, or is there a reliable encrypted, incremental backup alternative?

---

### Post by highflyr on 2010-10-20
This link is a bit old, but it may help. 

[http://ubuntuforums.org/showthread.php?t=1048637]("http://ubuntuforums.org/showthread.php?t=1048637")

I had an NTFS disk that I couldn't get restored while encrypted. Using unencrypted recovery works fine for me in 10.04 with deja dup.

---

### Post by soldier1st on 2010-10-22
did you try luckybackup?

---

### Post by Dave M G on 2010-10-22
Soldier1st,

Thank you for the suggestion. Unfortunately, according to their home page, luckyBackup does not support encryption.

highflyr,

Thank you for the link.

I read through the information there, but could not determine anything that would apply to my situation. Except that the developer of Deja Dup was active in that thread, so I might try contacting him.


Right now it looks like the only viable alternative option with all the features I hope for is rsyncrypto, but it is only available via command line, and I hate using the command line for this type of task.

---

### Post by highflyr on 2010-10-28
Yeah, I meant to point that out. It seems the encryption issue is alive and well. 

What about remastersys and encrypt the .iso..?   
[http://www.geekconnection.org/remastersys/index.html](http://www.geekconnection.org/remastersys/index.html)

---

### Post by Dave M G on 2010-10-28
Lynksis,

Thanks for the remastersys tip, but it seems a little unwieldy for what I'm trying to accomplish.

I want to be able to back up my whole home directory, so dealing in .iso files would seem to me to require breaking the process up into extra steps.

I think the problem here is that I'm just a little ahead of the curve in what's available. Encryption will probably be a standard feature in all these back up tools, but they aren't there yet.

It's frustrating to have to wait, but what can you do?

I appreciate all the work that has made these software applications available in the first place, so it's just a matter of waiting and hoping, I guess.

---

### Post by Dave M G on 2011-05-10
Solution: Abandoned Deja Dup and I'm now using Spideroak services.

---

### Post by Roasted on 2011-05-17
> **Dave M G said:**
> Solution: Abandoned Deja Dup and I'm now using Spideroak services.

That's a shame. I just discovered Deja Dup after hearing it may be included in 11.10 by default (as well as Fedora 13) and I have been loving it. I haven't been using encryption on my backups, but I've tried to break the backup/restore process but it always works for me. I used to be very nervous of compressed backups, and preferred to just sync the raw data and be done with it. But this isn't a bad idea at all.

Spideroak services - isn't that entirely online? Or do they have options for backups locally and whatnot?

I hope that you re-visit Deja Dup in time. From what I've read, it's come out of no where with reviews and more support. I haven't heard of it till a few days ago and it seems to be popping up more and more.

---

### Post by Dave M G on 2011-05-18
Roasted,

*SpiderOak* doesn't seem to do anything local, but in my situation, I use *Back In Time* for a non-encrypted local backup to an external USB drive.

Personally, the ultimate solution in my opinion is for *Back In Time* to offer encryption as one of its features. I personally favour the *Back In Time* interface over *Deja Dup* by quite a bit, especially when it comes to finding individual files for restoring.

Also, I've learned from my experience with *SpiderOak* that encryption eats up time in a big way, so it's probably not *Deja Dup*'s fault that my back up was taking so long. The fact is that if you're going to encrypt a 100 GB of data, be prepared for it to take days to make that initial backup.

Where *Deja Dup* was failing was in not being able to maintain the FTP connection or reconnect during the inevitable lengthy initial backup. And every time it failed, it had no ability to pick up from where it left off.

I signed up with *SpiderOak* for one year. If by then *Deja Dup* or *Back In Time* offer features that allow me to simplify my backup process, then I might switch over.

---

