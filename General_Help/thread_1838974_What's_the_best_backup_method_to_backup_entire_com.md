---
title: "What's the best backup method to backup entire computer?"
date: 2011-09-04
forum: General Help
---

### Post by pretty_whistle on 2011-09-04
I have only Ubuntu 11.04 on my laptop and I want to know best way to backup the entire PC.

What's the best and quickest way to back it up?

Limitation I have is I have no other computer to back it up on to.  I'd be using a portable hard drive for storing the backup.

When I had Windows (yuk! :) ) I made a disk image which took only 37 minutes to make.  Can I do this with Ubuntu in some way?  The program I used on Windows won't make a disk image of Linux- it only makes a raw image but that takes 4 hours to make it!

I need something, but what?

And certainly something that doesn't take 4 hours to make.

---

### Post by Chiel92 on 2011-09-04
> **pretty_whistle said:**
> I have only Ubuntu 11.04 on my laptop and I want to know best way to backup the entire PC.

What's the best and quickest way to back it up?

Limitation I have is I have no other computer to back it up on to.  I'd be using a portable hard drive for storing the backup.

When I had Windows (yuk! :) ) I made a disk image which took only 37 minutes to make.  Can I do this with Ubuntu in some way?  The program I used on Windows won't make a disk image of Linux- it only makes a raw image but that takes 4 hours to make it!

I need something, but what?

And certainly something that doesn't take 4 hours to make.

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

---

### Post by howefield on 2011-09-04
I like Clonezilla which will image your hard drive to your portable drive.

clonezilla.org

---

### Post by aura7 on 2011-09-04
Use Deja Dup. It is available in Synaptic.

[https://launchpad.net/deja-dup](https://launchpad.net/deja-dup)

---

### Post by pretty_whistle on 2011-09-04
> **Chiel92 said:**
> [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)


I saw that one.  But I have a question about how to make it save to a portable hard drive, like what to type in.

---

### Post by pretty_whistle on 2011-09-04
> **howefield said:**
> I like Clonezilla which will image your hard drive to your portable drive.

clonezilla.org


I have that in mind.  An image??  Is that a disk image, raw image, ? What kind?  About how long did it take on yours?

---

### Post by HousieMousie2 on 2011-09-04
Not to hijack, but how can a full disk image be created in 37 minutes?  How big is the hard drive?  dd with gzip takes several hours for a 250Gb HD... but it is bit for bit and compressed.

---

### Post by sammiev on 2011-09-04
+1 for Clonezilla.

It's fast and aways gave me 100% working images of all OS at the same time. Backups for me are about 32 min and a restore takes a little less.

---

### Post by pretty_whistle on 2011-09-04
> **HousieMousie2 said:**
> Not to hijack, but how can a full disk image be created in 37 minutes?  How big is the hard drive?  dd with gzip takes several hours for a 250Gb HD... but it is bit for bit and compressed.
I had used a disk imaging program and was making a disk image of Windows 7.  "C" drive was about 140GB in size but only about 75GB was used.  Compression was set to 'normal', whatever that meant.

---

### Post by pretty_whistle on 2011-09-04
> **sammiev said:**
> +1 for Clonezilla.

It's fast and aways gave me 100% working images of all OS at the same time. Backups for me are about 32 min and a restore takes a little less.

Cool.  Thanks.

I've already made a clonezilla CD to boot with and this seems to be the best option I think.

---

### Post by pretty_whistle on 2011-09-04
> **sammiev said:**
> +1 for Clonezilla.

It's fast and aways gave me 100% working images of all OS at the same time. Backups for me are about 32 min and a restore takes a little less.

What kind of image do you make?  I've heard of disk image, raw image, clone, and I forget another one I've heard of.

---

### Post by pretty_whistle on 2011-09-04
Update:

I just used clonezilla and it took 25.5 minutes to make a disk image and verify it.

Cool.

Consider this thread solved.

Thanks for everyone's input!

---

### Post by sammiev on 2011-09-04
Now you have a great backup, you can test anything you wish to as you can always return to your latest backup. I backup about every 2 weeks. GL :)

---

### Post by howefield on 2011-09-05
> **pretty_whistle said:**
> I have that in mind.  An image??  Is that a disk image, raw image, ? What kind?  About how long did it take on yours?

It will image only the used sectors on the disk, similar to Norton Ghost or Acronis True Image.

Takes me about 6 minutes to clone 2 operating systems and a little less to use the resultant images to restore. Both ext4 systems, 500 gig disk with about 16 gig of used space.

Edit: just noticed the replies above. Congrats.

---

