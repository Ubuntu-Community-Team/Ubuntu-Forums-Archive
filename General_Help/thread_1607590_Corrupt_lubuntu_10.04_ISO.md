---
title: "Corrupt lubuntu 10.04 ISO"
date: 2010-10-27
forum: General Help
---

### Post by papibe on 2010-10-27
I've download twice the lubuntu-10.04.iso (using torrent) and both times I'm getting this error when I check the disk:
```
Check Finished: errors found in 1 files!
```

I've even mounted the iso file on VirtualBox (before burn it), and I got the same result.

I appreciate any help,
Thanks in advance.

---

### Post by ericdn on 2010-10-27
> **papibe said:**
> I've download twice the lubuntu-10.04.iso (using torrent) and both times I'm getting this error when I check the disk:
```
Check Finished: errors found in 1 files!
```

I've even mounted the iso file on VirtualBox (before burn it), and I got the same result.

I appreciate any help,
Thanks in advance.

Maybe you happened to acquire a faulty file?  What's the source you used?  Try going to the official Lubuntu page at [http://lubuntu.net/]("http://lubuntu.net/") and get the install file directly from the source.

---

### Post by papibe on 2010-10-28
Thanks ericdn, but I got it from there. The torrent file that is (they highly recommended it, as opposed to direct download).

Any other idea?

---

### Post by Quackers on 2010-10-28
Check the MD5 checksum to make sure the downloaded file is correct. If it is then you are likely to be suffering from a bad burn. Try burning the image at the slowest speed setting.

---

### Post by vim_lover on 2010-10-28
The md5 sum for lubuntu-10.04.iso is _[http://people.ubuntu.com/~gilir/md5sum.txt]("http://people.ubuntu.com/%7Egilir/md5sum.txt")_

386a227968cbabc89e1a23b95035160e  lubuntu-10.04.iso
 
Note the output of the following code
```

md5sum lubuntu-10.04.iso
```

---

### Post by papibe on 2010-10-28
Thanks Quackers, I got the sums [here]("http://people.ubuntu.com/~gilir/md5sum.txt"). Although the ISO has the correct sum, I still get the error when I select "Check disk for defects".

The above is valid for the image iso file (before any burn). And also valid for two burned CDs.

---

### Post by ssulaco on 2010-10-28
You might try these,not sure if they are coming from the same location...
[https://wiki.ubuntu.com/Lubuntu#Get%20Lubuntu](https://wiki.ubuntu.com/Lubuntu#Get%20Lubuntu)
Have you tried the iso in another computer?

---

### Post by asifnaz on 2010-10-28
Well I had the same error for Lubuntu . But I installed that that cd and it worked perfectly . ( I am writing this using that Lubuntu ) . I am a new user ..but I will suggest you to install from that cd hopefully it will work .

---

### Post by mastablasta on 2010-10-28
> **papibe said:**
>  And also valid for two burned CDs.

if md5sum is still ok after you burn then the CD then it is probably all ok.

It might be that whatever software is flagging the error that it is a "false positive"/false alarm.

---

### Post by Old_Man_Unix on 2010-10-28
Brasero - and most applications that burn .iso images - have a verified burn plug-in or setting that is normally enabled or turned on by default.  If that plug-in is not enabled in your Brasero configuration,  please do that.  Other programs may turn on that setting in different ways so you will have to refer to your manual. 

If your .iso download checks out OK -  using md5sum - **and** you use the verified burn setting  on your burning application, you can be sure that your disk is fine.

If you load the disk and boot it, and then use the option on the boot menu to check the disk, you will sometimes get the "false positive" as previously mentioned.  But if you have done everything correctly up to that point, don't worry about it.  

As you may know, you generally cannot use the  .iso file checksum to  directly verify the disk due to padding.  I'm not saying that is what is happening, I am just mentioning it.

---

### Post by papibe on 2010-10-28
> You might try these,not sure if they are coming from the same location...
[https://wiki.ubuntu.com/Lubuntu#Get%20Lubuntu](https://wiki.ubuntu.com/Lubuntu#Get%20Lubuntu)

That's the place I got it from.
> Have you tried the iso in another computer?
Yes, first download on a laptop, and a desktop. Second one on a third desktop. All with the same result.

---

### Post by papibe on 2010-10-28
I decided to proceed with the install anyway, and it worked fine. Thanks to all for your tips and advices.

When I started the thread, I thought I checked all info about this release in the Lubuntu official [blog]("http://lubuntu.net/blog/lubuntu-1004-now-available-download"). If you read the blog post, you won't find any hint about the problem I was having.

Today I check again, but this time I went and read the user comments. Surprise, surprise, in just the first page there's at least 7 comments about the problem. :confused:

Any way, thanks again!

---

### Post by asifnaz on 2010-10-29
> **papibe said:**
> I decided to proceed with the install anyway, and it worked fine. Thanks to all for your tips and advices.

When I started the thread, I thought I checked all info about this release in the Lubuntu official [blog]("http://lubuntu.net/blog/lubuntu-1004-now-available-download"). If you read the blog post, you won't find any hint about the problem I was having.

Today I check again, but this time I went and read the user comments. Surprise, surprise, in just the first page there's at least 7 comments about the problem. :confused:

Any way, thanks again!

Didnt I told you it will work

---

