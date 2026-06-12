---
title: "Complete system backup in case of hard drive failure"
date: 2011-01-29
forum: General Help
---

### Post by epud on 2011-01-29
**Hello!**

I have been researching the web for a program which will allow me to backup my entire hard drive so that I can restore my system if need be. I am however unsure which is the best one to use if I want to achieve this:

Somehow I want to back up my hard drive containing my ubuntu system byte for byte so that if the hard drive were to fail I could simply go to the store, get a new hard drive, restore my backup and be up and running again without having to do any re installments of ubuntu or any other programs for that matter.

What is the easiest program that does this? I would like it to support incremental backup.

**rsync** with the "Back in Time interface"?
**bacula**?
ps. Clonezilla (does not support incremental backup) thus not an option.

Thank you for your time

---

### Post by sydbat on 2011-01-29
[Remastersys]("http://remastersys.sourceforge.net/").

---

### Post by epud on 2011-01-29
Great! I will give it a try. But does it do an incremental backup? Or do I every time I back up get stuck with a big file?

Thank you

---

### Post by AlanR8 on 2011-01-29
The other option is to put all your data on line somewhere and use Gmail as your mail client!

That's how I've been for the last couple of years and I don't care if I have to rebuild because of an error (on my part)! All my data is remote.

I use Dropbox for my syncing and I regret to confess Microsoft SkyDrive for the stuff that's static. 

25 Gigs for free from Bill and Steve Balmer....

---

### Post by ezsit on 2011-01-29
Remastersys is used to create a live CD or DVD from your existing system. It is a backup, but the limit is 4.3GB total, so if you are backing up all your data and it totals more than the size of a DVD including the entire operating system, then you are out of luck. 

I use Remastersys to produce a distribution from my installed system and backup my personal files to external hardrives. This way I always have a reinstallation DVD with all my programs installed and I have my data separately backed up.

You can try "Deja Dup" for the data backup if you want to create a backup profile and run incremental backups at regularly scheduled intervals. I just TAR up my data folders and drag them to the external drive every week or so.

---

### Post by steve7777777 on 2011-01-29
> **epud said:**
> **Hello!**

I have been researching the web for a program which will allow me to backup my entire hard drive so that I can restore my system if need be. I am however unsure which is the best one to use if I want to achieve this:

Somehow I want to back up my hard drive containing my ubuntu system byte for byte so that if the hard drive were to fail I could simply go to the store, get a new hard drive, restore my backup and be up and running again without having to do any re installments of ubuntu or any other programs for that matter.

What is the easiest program that does this? I would like it to support incremental backup.

**rsync** with the "Back in Time interface"?
**bacula**?
ps. Clonezilla (does not support incremental backup) thus not an option.

Thank you for your time

I wouldn't write off Clonezilla so fast. 

I create an image of SDA1 with Clonezilla once a week or so  and do incremental backups of   **/home** and **/etc**. I think I'm covered. If there's a problem I can restore the Clonezilla image to a new disk, followed by  **/home** and [B]/etc. 

[/B]Does this sound like a viable backup strategy?

---

### Post by epud on 2011-01-29
Hi steve7777777

That sounds like a really good strategy. I think I will give that a try. Thanks!

---

### Post by epud on 2011-01-29
> **AlanR8 said:**
> The other option is to put all your data on line somewhere and use Gmail as your mail client!

That's how I've been for the last couple of years and I don't care if I have to rebuild because of an error (on my part)! All my data is remote.

I use Dropbox for my syncing and I regret to confess Microsoft SkyDrive for the stuff that's static. 

25 Gigs for free from Bill and Steve Balmer....

Hi AlanR8

For me it is not about syncing files online. I do that all the time in other ways such as an online ftp server and google docs, ubuntu one etc... What I was looking for was to make a backup such that if someone right now ripped out my 64 Gig system disk (with ubuntu on it) and smashed it with a hammer I would still be able to recover my entire operating system with all it's settings and tweaks my buying a new hard drive and loading the backup onto it without having to reinstall anything.

---

### Post by tredegar on 2011-01-29
Off-topic warning:

> The other option is to put **[COLOR="Red"]all your data on line somewhere[/COLOR]** and use Gmail as your mail client!

Do you realise that Gmail reads, cross-indexes, considers and categorises your emails, and any data you pass to them? 

Some time into the future you might regret having given away quite so much personal information. Times change and not always for the better.
> 25 Gigs for free from Bill and Steve Balmer....
I have seen nothing from them that is truly "free". There's *always* a price to pay, but did you notice what it was, have you read and really understood the small print, and what that *could* mean?

Be careful.

---

