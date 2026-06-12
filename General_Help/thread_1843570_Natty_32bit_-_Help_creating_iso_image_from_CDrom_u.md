---
title: "Natty 32bit - Help creating iso image from CDrom using Cli"
date: 2011-09-13
forum: General Help
---

### Post by AlexOnVinyl on 2011-09-13
Hi there,

I seem to be running into issues as I try to use the CLi to create an iso image of a cdrom that I have in my drive.

Here's what I've tried so far:

```
alex@griever:~$ dd** if=/dev/cdrom** of=~/disc1.iso
dd: reading `/dev/cdrom': Input/output error
48+0 records in
48+0 records out
24576 bytes (25 kB) copied, 0.00641352 s, 3.8 MB/s
alex@griever:~$ dd **if=/dev/scd0** of=cd.iso
dd: reading `/dev/scd0': Input/output error
48+0 records in
48+0 records out
24576 bytes (25 kB) copied, 0.00656128 s, 3.7 MB/s
alex@griever:~$ 

```

As you can see I've tried both /dev/cdrom and /dev/scd0 and didn't really get very far.

Could someone help tell me what I'm doing wrong?:confused:

---

### Post by coffeecat on 2011-09-13
> **AlexOnVinyl said:**
> As you can see I've tried both /dev/cdrom and /dev/scd0 and didn't really get very far.

They're both symlinks to /dev/sr0 which usually works for me. I don't know why the symlinks don't work, but try:

```
sudo dd if=/dev/sr0 of=path/to/file.iso
```

---

### Post by AlexOnVinyl on 2011-09-13
> **coffeecat said:**
> They're both symlinks to /dev/sr0 which usually works for me. I don't know why the symlinks don't work, but try:

```
sudo dd if=/dev/sr0 of=path/to/file.iso
```

can you give me an example of what to put in for the Path to file?

---

### Post by AlexOnVinyl on 2011-09-13
> **coffeecat said:**
> They're both symlinks to /dev/sr0 which usually works for me. I don't know why the symlinks don't work, but try:

```
sudo dd if=/dev/sr0 of=path/to/file.iso
```

Oh I see what you changed... the /sr0 part

got it, let me give it a try.:D

-----

Yep, still got the same issue:

```
alex@griever:~$ sudo dd if=/dev/sr0 of=~/disc1.iso
dd: reading `/dev/sr0': Input/output error
48+0 records in
48+0 records out
24576 bytes (25 kB) copied, 0.00653128 s, 3.8 MB/s
alex@griever:~$ 

```

---

### Post by coffeecat on 2011-09-13
To be honest, I'm mystified. I wonder if the cdrom is faulty. Try with another CDROM. If dd works with another cdrom, then the one you are trying to copy may be faulty. Or try Brasero or k3b - both GUI apps. If you use Brasero, you choose "Create a 1:1 copy of a CD" and then specify an ISO as output.

---

### Post by AlexOnVinyl on 2011-09-13
> **coffeecat said:**
> To be honest, I'm mystified. I wonder if the cdrom is faulty. Try with another CDROM. If dd works with another cdrom, then the one you are trying to copy may be faulty. Or try Brasero or k3b - both GUI apps. If you use Brasero, you choose "Create a 1:1 copy of a CD" and then specify an ISO as output.

that's weird that you would think it would be faulty, because I can read and write things to and from it just fine.

ill try brasero

and ill reply back.

Wait did you mean the CDrom? or my cd drive? because I've been able to write things to cdroms and dvds just fine.

---

### Post by coffeecat on 2011-09-13
> **AlexOnVinyl said:**
> that's weird that you would think it would be faulty, because I can read and write things to and from it just fine.

ill try brasero

and ill reply back.

Wait did you mean the CDrom? or my cd drive? because I've been able to write things to cdroms and dvds just fine.

Yes, I was careless with my terminology. I was wondering if the actual CD disc was faulty. But a misreading optical drive could be another possibility.

---

### Post by AlexOnVinyl on 2011-09-13
> **coffeecat said:**
> Yes, I was careless with my terminology. I was wondering if the actual CD disc was faulty. But a misreading optical drive could be another possibility.

Just got done trying using it.  It read it and started copy to an image file,

I dont believe that if it was an actual issue with my drive that it would be able to burn files and images to cds like I have been, right? I mean if it was an issue with the drive, I dont think it'd read it at all.

---

### Post by coffeecat on 2011-09-13
> **AlexOnVinyl said:**
> I dont believe that if it was an actual issue with my drive that it would be able to burn files and images to cds like I have been, right? I mean if it was an issue with the drive, I dont think it'd read it at all.

Well.... I have a SATA CD/DVD drive that occasionally goes all moody on me. :) Most of the time it works well <snip>.

I have no idea what is going on there. :|

---

### Post by AlexOnVinyl on 2011-09-13
> **coffeecat said:**
> Well.... I have a SATA CD/DVD drive that occasionally goes all moody on me.<snip>.

I have no idea what is going on there. :|

I ran a few tests that you can look at on my video I made. they may help you help me identify the issue:

----
**For some reason the audio when it was processed decided to go fast and near chipmunk like. but either way, you'll still get to see what im talking about... Sorry for the shotty video o.O**
It may still be being processed, so give it a minute: [http://www.youtube.com/watch?v=X-654IJnpGw](http://www.youtube.com/watch?v=X-654IJnpGw)

---

### Post by coffeecat on 2011-09-13
I've only watched the video once as it's very late here, but it seemed as though Brasero was working. Am I correct?

When you did something like:

```
sudo if=/dev/cdrom0 of=~/file.iso
```

It quickly errored. But when you did:

```
sudo if=/dev/cdrom0 of=file.iso
```

You got an ISO in your home folder. Was it OK? Because if so, it seems that the tilda (~) is upsetting dd.

Just a thought. I must log off in a few minutes and I'll come back to this thread in the morning (UK time).

---

### Post by AlexOnVinyl on 2011-09-13
> **coffeecat said:**
> I've only watched the video once as it's very late here, but it seemed as though Brasero was working. Am I correct?

When you did something like:

```
sudo if=/dev/cdrom0 of=~/file.iso
```It quickly errored. But when you did:

```
sudo if=/dev/cdrom0 of=file.iso
```You got an ISO in your home folder. Was it OK? Because if so, it seems that the tilda (~) is upsetting dd.

Just a thought. I must log off in a few minutes and I'll come back to this thread in the morning (UK time).

Both of them gave me errors. I didnt try without the tilda, ill give it a go then update the thread.

----------------------------------
**UPDATE 4:02PM 9/13/11**
Here's what I tried 
```
alex@griever:~$ sudo dd if=/dev/cdrom of=/disc1.iso
[sudo] password for alex: 
dd: reading `/dev/cdrom': Input/output error
48+0 records in
48+0 records out
24576 bytes (25 kB) copied, 3.45497 s, 7.1 kB/s
alex@griever:~$ sudo dd if=/dev/sr0 of=/disc1.iso
dd: reading `/dev/sr0': Input/output error
48+0 records in
48+0 records out
24576 bytes (25 kB) copied, 0.00492048 s, 5.0 MB/s
alex@griever:~$ dd if=/dev/scd0 of=/cd.iso
dd: opening `/cd.iso': Permission denied
alex@griever:~$ sudo dd if=/dev/scd0 of=/cd.iso
dd: reading `/dev/scd0': Input/output error
48+0 records in
48+0 records out
24576 bytes (25 kB) copied, 0.0064936 s, 3.8 MB/s
```

I tried all three of those and for some reason it keeps giving me a reading error of that drive,
but even with or without the tilda I get the same issue.
**it still creates an image (.iso) file but the file is blank, no data what so ever.**

---

### Post by AlexOnVinyl on 2011-09-13
Okay. so I found something intriguing - I was looking around and I found out that certain cds are written with multitracks - eg: playstation cds. the data is written to "Playstation-Cd's because the data track is written in mode 2 which dd can't read, and because the Cd's are multitrack (one data-track and several audio-tracks)."(13 September 2011)
[URL="http://linuxreviews.org/howtos/cdrecording/"] http://linuxreviews.org/howtos/cdrecording/
[/URL]
according to the article, I'm going to have to do this:

```
cdrdao read-cd --read-raw --datafile [filename.bin] --device [bus,id,lun] --driver generic-mmc-raw [filename.toc]
```


[B]
[/B]

---

### Post by bapoumba on 2011-09-14
Last post in this thread shows the questions were related to an activity we wont support here.

---

