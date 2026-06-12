---
title: "disk burning always results in md5sum errors"
date: 2009-08-11
forum: General Help
---

### Post by rayj on 2009-08-11
Hello, everyone.

Several weeks ago, my system suddenly became incapable of burning .iso's without resulting in an error. It runs through the burn processes smoothly, but any md5sum checks result in an error.

I've reinstalled my entire OS (8.04) several times, and yet still have these persistant burn errors. The checksum for the local .iso image is fine. I've tried everything I can...burning at the slowest speeds, installing and using several burning suites (k3b, gnome-baker, etc.), and haven't had a single successful burn yet.

Has anyone had this sort of issue? I don't even know how to go about diagnosing it. My thoughts are that either my media is crap, or one of the recent updates has hosed the burning process for my hardware. I've even tried buying and installing a new DVD drive, and yet the errors persist. This is causing me a whole host of issues...

Any suggestions would be greatly appreciated. Thanks in advance...

---

### Post by jocampo on 2009-08-11
> **rayj said:**
> Hello, everyone.

Several weeks ago, my system suddenly became incapable of burning .iso's without resulting in an error. It runs through the burn processes smoothly, but any md5sum checks result in an error.

I've reinstalled my entire OS (8.04) several times, and yet still have these persistant burn errors. The checksum for the local .iso image is fine. I've tried everything I can...burning at the slowest speeds, installing and using several burning suites (k3b, gnome-baker, etc.), and haven't had a single successful burn yet.

Has anyone had this sort of issue? I don't even know how to go about diagnosing it. My thoughts are that either my media is crap, or one of the recent updates has hosed the burning process for my hardware. I've even tried buying and installing a new DVD drive, and yet the errors persist. This is causing me a whole host of issues...

Any suggestions would be greatly appreciated. Thanks in advance...

If you changed the the drive, I doubt is hardware issue. Which software are you using, Brasero? try to uninstall for good your CD Burning software, then re-install and try again ... something like this

```
>sudo apt-get --purge remove <package>
```
```
>sudo apt-get clean
```

---

### Post by hangfire on 2009-08-11
Since upgrading from K8.04/64bit to K9.04/32bit I have found that most of my K3b burns result in an md5sum mismatch on verify (I always verify).

Running 

```
md5sum /dev/sr0
```

usually returns the correct md5sum, despite what verify says. I am learning not to trust the K3b verify option. :(

Like you, I replaced my burner trying to address this issue, and finally realized all my cd-r's were good and it was a software issue.

-HF

---

### Post by Sef on 2009-08-11
> If you changed the the drive, I doubt is hardware issue. Which software are you using, Brasero? try to uninstall for good your CD Burning software, then re-install and try again

Try another burn software.   I use gnomebaker, which you can add through Add/Remove.  Just make sure Show is set to either All Open Source Applications or All Available Applications.

---

### Post by rayj on 2009-08-11
Thanks for the quick replies!

Per my message, I've tried 3 different burning suites, to no avail. I always verify my md5sums via the command line...

Not to mention, that I've reinstalled my entire OS at least 3 times. I assumed it was some obscure viral code...but that obviously isn't the case.

The only thing I haven't tried to date is changing my media (some brand of Memorex DVD+R). I'll try a different media tonight...if that actually is the issue, I'll post the details on my batch of media here.

Any other suggestions on how to diagnose the issue?

---

### Post by jocampo on 2009-08-11
Could be the media, yeah! There are crappy companies out there with poor quality control ;-) ... I remember one day that I tried like 3 different CDs, all of them were bad ... fourth one worked and was NOT my drive.

I find k3b a good software but problem is that if you're using Gnome, you will have to install some additional libraries which will use extra space. Like I said  before, uninstall and re-install the CD burning software and try with same media. If fails again, DO NOT CHANGE software, try with another brand and see what happen. If still same issue...then remove and try another cd burning software ..

---

### Post by rayj on 2009-08-12
Still getting these errors...

I'm disinclined to think that it is a media problem, simply because the failed md5sum I am getting back on all of my bad burns has resulted in the exact same hash. Does anyone know if that's an accurate assumption?

Still fishing for suggestions here...I've been wrestling with this issue for weeks now.

Thanks in advance...

---

### Post by rayj on 2009-08-13
...I'm starting to suspect some other hardware issue. Unfortunately, I'm not sure where to begin when it comes to diagnosing the problem...the logs don't really provide any useful hints, at least for someone with my relatively scant understanding of GNU/Linux in general.

Still fishing for suggestions...nothing mentioned above has helped, and I've tried them all. Any help would be appreciated...I'm not afraid of the command line...

---

### Post by Maheriano on 2009-08-13
I get the same errors. I fixed it by using a different type of CD to burn to. For some reason I have a pack of cheap CD that will not return the correct MD5 when checked.

---

### Post by trundlenut on 2009-08-13
the lens isn't dirty on the burner is it?

I recently installed ubuntu server onto a machine I picked up and couldn't work out why it was giving me loads of MD5/file corrupted errors - then I looked into the tray on the burner and there was rather a lot of dust in there.  Quick clean and it all worked fine.

Though I would say if this was a sudden change it would suggest some sort of hardware failure, especially given everything else you have changed, any chance you could swap the drive with one from another machine?

---

### Post by michy99 on 2009-08-13
> **rayj said:**
> Still getting these errors...

I'm disinclined to think that it is a media problem, simply because the failed md5sum I am getting back on all of my bad burns has resulted in the exact same hash. Does anyone know if that's an accurate assumption?

Still fishing for suggestions here...I've been wrestling with this issue for weeks now.

Thanks in advance...

Does that mean you have been trying this with the same file every time? Have you tried burning a different file to see if it is just this file which is causing problems?

Also, I may have missed this, but does the resulting CD appear to work, even though it is returning a checksum error?

---

### Post by Maheriano on 2009-08-13
> **trundlenut said:**
> the lens isn't dirty on the burner is it?

I recently installed ubuntu server onto a machine I picked up and couldn't work out why it was giving me loads of MD5/file corrupted errors - then I looked into the tray on the burner and there was rather a lot of dust in there.  Quick clean and it all worked fine.

Though I would say if this was a sudden change it would suggest some sort of hardware failure, especially given everything else you have changed, any chance you could swap the drive with one from another machine?

> **rayj said:**
> I've even tried buying and installing a new DVD drive, and yet the errors persist.
:confused:

---

### Post by trundlenut on 2009-08-13
#-o

that'll teach me to read while tired.

---

### Post by pizmooz on 2009-08-13
Even though it seems unlikely I wouldn't rule out a cable or bus issue.  Be it IDE,USB or SCSI try changing your cable into a different port on the board and trying again.  If that doesn't work try swapping out the cable also.  Additionally 'tail -f dmesg' in a terminal while you are burning and see if you see anything suspect pop up.

---

### Post by rayj on 2009-08-14
> **michy99 said:**
> Does that mean you have been trying this with the same file every time? Have you tried burning a different file to see if it is just this file which is causing problems?

It has been the same with several different .iso's, for several different distros. I went whacko and decided to try out a bunch all at once, without really having the slightest idea what I was doing.

> Also, I may have missed this, but does the resulting CD appear to work, even though it is returning a checksum error?

Every OS (Studio 64 - 32bit AND 64bit, Sidux) that I've burned has worked just fine so far, to a point. It is difficult without running full tests (I'd have to learn how to do that...and what 'that' is...etc.) to determine what a particular 'issue' might be (standard live distro weirdness corrupted .iso files/bad burns, misunderstood features, or whatever).

None of those disks pass a disk integrity self-test.

I'm going to try the cable swap, and see if I can make heads or tails of dmesg.

---

### Post by venturosa on 2009-08-16
I've had a recent problem burning iso images to dvd. Brasero reports an error and says that some files may be currupted. On playing the dvd (movie) on the computer (ubuntu jaunty) the fault shows up and the movie hangs. After wasting three dvds on this I put one of them in my 'stand alone' dvd player and found it played perfectly right through. I then put it on a windows computer where it also worked perfectly.
I've always used Brasero for burning isos and never had a problem before. All this points, IMHO, to the operating system because this problem has only appeared since I installed jaunty (clean install).

---

