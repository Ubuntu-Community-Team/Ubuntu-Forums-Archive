---
title: "Amazon Glacier service for backups on Ubuntu?"
date: 2012-08-25
forum: General Help
---

### Post by amac777 on 2012-08-25
Does anyone know if there is a Ubuntu tool yet for storing archives using Amazon Glacier? 

[http://aws.amazon.com/glacier/](http://aws.amazon.com/glacier/)

The price point for Glacier seems to be low enough, $0.01 USD per gig/month, I'm considering archiving my photo collection on there as an offsite backup, but hoping there is something like rsync to do it.

---

### Post by amac777 on 2012-08-30
bump

---

### Post by Habitual on 2012-08-30
"If you need to retrieve an archive, you initiate a job that will typically complete in 3.5 to 4.5 hours." says [http://www.i-programmer.info/news/141-cloud-computing/4682-amazon-glacier-for-cold-storage.html](http://www.i-programmer.info/news/141-cloud-computing/4682-amazon-glacier-for-cold-storage.html)

Unacceptable at any price.

---

### Post by amac777 on 2012-08-30
I'm thinking of a long term backup of my my photos and videos. In the event my house burns down and all my local backups are destroyed, still have the online version. Priceless family photos/videos etc. A penny a gig per month for the long term backup, and a couple months of slowly downloading them for free in the event of a disaster is a very acceptable price for me... Just trying to find an easy way to use the service.

---

### Post by tiagolramos on 2012-08-31
> **Habitual said:**
> "If you need to retrieve an archive, you initiate a job that will typically complete in 3.5 to 4.5 hours." says [http://www.i-programmer.info/news/141-cloud-computing/4682-amazon-glacier-for-cold-storage.html](http://www.i-programmer.info/news/141-cloud-computing/4682-amazon-glacier-for-cold-storage.html)

Unacceptable at any price.

You have never used off premises storages, this is to replace tapes and physical.

read the  Use Cases this isn't S3

[http://aws.amazon.com/en/glacier/](http://aws.amazon.com/en/glacier/)

---

### Post by amac777 on 2012-08-31
Yeah, it's not S3 in terms of speed.... but it's much cheaper for long term archival and as long as you don't request a lot of data at once it is very cheap (even free) for retrieval.

I've been searching for tools to use glacier with ubuntu but the stuff I've found all requires too much programming and fiddling to get working. I suspect it's just too soon after the amazon announcement so not enough time for people to develop GUI and CLI tools yet. I'm excited to see some stuff for glacier showing up in the repositories...

---

### Post by Balachmar on 2012-09-01
It seems that the boto guys are already working on it. Boto is the layer which is used by Deja Dup, the default backup utility.
I agree that this would be a great way to backup the stuff that doesn't change, like pictures etc.
The only reason why I would want to use it, is as an off site backup for the things I really don't want to lose.
For the rest I use my home brew NAS.

---

### Post by h_corey on 2012-09-01
[https://github.com/MoriTanosuke/glacieruploader](https://github.com/MoriTanosuke/glacieruploader)

This works on Ubuntu

---

### Post by amac777 on 2012-09-01
Balachmar, yeah, hopefully the Deja Dup team will add glacier support. That's pretty much what I'm looking for now that you mention it. Thanks for pointing out that program. I'm still on ubuntu 10.04 and it was not installed by default as far as I know. I also have very good local backups (mine using rsnapshot), but I'd still like a long term "just in case" cloud backup for the family photos and videos.

h_corey, I saw a few things on github that might work on ubuntu including the one you pointed out. I got as far as downloading it but did not figure how it works. Did you get it working?

---

### Post by DaveQB on 2012-11-15
And for a GUI

[http://simpleglacieruploader.brianmcmichael.com/](http://simpleglacieruploader.brianmcmichael.com/)

It is Java also.

---

### Post by Parama on 2012-11-23
This solution is Python-based and not exactly rocket science

[http://www.withoutthesarcasm.com/?p=457](http://www.withoutthesarcasm.com/?p=457)

---

### Post by sdowney717 on 2012-11-23
how about using google drive for no cost?
[https://www.google.com/intl/en_US/drive/start/index.html?authuser=0](https://www.google.com/intl/en_US/drive/start/index.html?authuser=0)
I already back uo some pictures there.

---

### Post by sdowney717 on 2012-11-23
[http://www.omgubuntu.co.uk/2012/08/insync-brings-google-drive-to-ubuntu](http://www.omgubuntu.co.uk/2012/08/insync-brings-google-drive-to-ubuntu)

you can use insync integration into nautilus with google drive.
I need to try this.

---

### Post by Parama on 2012-12-04
> **sdowney717 said:**
> how about using google drive for no cost?

No! You and a lot of others are totally missing the point with Amazon Glacier. It is *not* a regular cloud storage for easy access. 
It's made from the bottom up as a store for backup data and the price is accordingly.
I have the need to backup 200GB of pictures I have personally taken in this millenium. If I use Google Drive I'll have to pay 240 USD/year whereas if I use Amazon Glacier I only have to pay a fifth or 48 USD/year. So I'm really looking forward to when Deja-Dup gets Glacier support.

I reckon that in the years to come the price per GB will get even lower on all cloud storage solutions, from Amazon S3, MS Skydrive, Apple iCloud and Google Drive to Amazon Glacier, but because of the way Glacier is made it will always cost at around a fifth compared to the regular cloud store solutions.

Here's a video on Youtube where a guy from Amazon gives a rather good explanation of what Glacier is: [http://youtu.be/4RrDbP9AUFA]("http://youtu.be/4RrDbP9AUFA")

---

### Post by DaveQB on 2012-12-04
> **Parama said:**
> No! You and a lot of others are totally missing the point with Amazon Glacier. It is *not* a regular cloud storage for easy access. 
It's made from the bottom up as a store for backup data and the price is accordingly.
I have the need to backup 200GB of pictures I have personally taken in this millenium. If I use Google Drive I'll have to pay 240 USD/year whereas if I use Amazon Glacier I only have to pay a fifth or 48 USD/year. So I'm really looking forward to when Deja-Dup gets Glacier support.

I reckon that in the years to come the price per GB will get even lower on all cloud storage solutions, from Amazon S3, MS Skydrive, Apple iCloud and Google Drive to Amazon Glacier, but because of the way Glacier is made it will always cost at around a fifth compared to the regular cloud store solutions.

Here's a video on Youtube where a guy from Amazon gives a rather good explanation of what Glacier is: [http://youtu.be/4RrDbP9AUFA]("http://youtu.be/4RrDbP9AUFA")

Exactly!
Glacier guarentee 99.999999999% of durability.

> 
the durability of an object stored in Amazon Glacier is 99.999999999%. If you store 10,000 objects with us, on average we may lose one of them every 10 million years or so. This storage is designed in such a way that we can sustain the concurrent loss of data in two separate storage facilities.


I don't know but I doubt google drive promises that.

[http://aws.amazon.com/glacier/#highlights](http://aws.amazon.com/glacier/#highlights)

Plus to get the data in there is [http://aws.amazon.com/importexport/](http://aws.amazon.com/importexport/)

---

