---
title: "Wrong MD5SUM on CDs burnt from ISOs"
date: 2010-01-13
forum: General Help
---

### Post by abovett on 2010-01-13
I am having a problem checking the MD5SUM of some CDs burnt from ISOs, and I'm not sure whether the problem is the burning or the checking. I get the same problems on several PCs, and it seems to be dependent on the ISO. I have for a couple of years used a script someone gave me to verify CDs against ISOs when I want to check the disc and it has always worked in the past. 

The core line in the script is: 
```
devmd5=`readom dev=$cddev sectors=0-$count f=- | md5sum | awk '{print $1}'
```
count is the size of the ORIGINAL ISO as calculated by isosize

For some ISOs the MD5SUM of the CD and the original ISO always matches, but for others I always get a different (but consistent) result. It's not that the ISO is too big, either - one that gave a different result is slightly smaller than one that worked OK.

I've tried burning the CDs from the command line (with wodim) and via K3B. When using K3B I selected the "verify" option and it verified OK but the script still says it's wrong.

Anyone know what's going on? Or suggest another way to check CDs? I'm not sure if I can trust my CDs any more!

Thanks

Andy

---

### Post by shreepads on 2010-01-13
Umm not an expert but will hazard a guess.

The .iso file is a representation of the contents on a disk (there are other possible representations). No reason why the md5sum of the .iso file should match the md5sum of the data stream from the CD.

Actually was quite suprised that it did match in the past for you...

One suggestion, generate a .iso image from your burned disk and run md5sum on that .iso image file. If this matches the md5sum on your original .iso you can be certain the burn went well.

---

### Post by sanderj on 2010-01-13
> **shreepads said:**
> Umm not an expert but will hazard a guess.

The .iso file is a representation of the contents on a disk (there are other possible representations). No reason why the md5sum of the .iso file should match the md5sum of the data stream from the CD.

Actually was quite suprised that it did match in the past for you...

One suggestion, generate a .iso image from your burned disk and run md5sum on that .iso image file. If this matches the md5sum on your original .iso you can be certain the burn went well.

I agree with your reasoning.

Another way to check:
1) download the ISO, and run md5sum on it to verify the ISO
2) then burn the CD, and let the burn program verify CD the afterwards
If both 1 and 2 are OK, you can be sure the CD is OK.

HTH

---

### Post by abovett on 2010-01-17
> **shreepads said:**
> No reason why the md5sum of the .iso file should match the md5sum of the data stream from the CD.

I believe that a .iso file is basically a bit-for-bit representation of the data on the CD, so I think it should match. I know other people have used this method for verifying CDs in the past (in fact one of them supplied me with the original script - must try to track down where it came from)

> 
Actually was quite suprised that it did match in the past for you...
Always has done until now when using this script.

> 
One suggestion, generate a .iso image from your burned disk and run md5sum on that .iso image file. If this matches the md5sum on your original .iso you can be certain the burn went well.
Sounds like a sensible suggestion. How would you suggest making the .iso - K3B?

Thanks

Andy

---

### Post by shreepads on 2010-01-18
> **abovett said:**
> 
Sounds like a sensible suggestion. How would you suggest making the .iso - K3B?


That or Brasero (as long as you are on Intrepid or above). Have a look at this [link]("https://answers.launchpad.net/ubuntu/+source/brasero/+question/55866")

Though I haven't done this myself!

---

### Post by Leppie on 2010-01-18
ubuntu comes with the md5sum application.
have a look at this page: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by abovett on 2010-01-21
> **shreepads said:**
> That or Brasero (as long as you are on Intrepid or above). Have a look at this [link]("https://answers.launchpad.net/ubuntu/+source/brasero/+question/55866")

Though I haven't done this myself!

Thanks.

I note that on the page you linked to some people suggest using:

```
dd if=/dev/cdrom of=<filename>.iso
```

This is effectively the same as the script I was using (which routed the data directly to md5sum rather than to a file). This suggests that other people, like I, have assumed that a .iso file is a raw dump of the data from the CD and that this has worked for them. Not sure if K3B or Brasero do anything more sophisticated. I'll do a little more investigating when I have time and post any results here in case anyone else is interested.

Cheers

Andy

---

### Post by Leppie on 2010-01-21
> **shreepads said:**
> No reason why the md5sum of the .iso file should match the md5sum of the data stream from the CD.
i have used md5sum to check both .iso files and the finished cd's. this is actually the suggested way in the ubuntu documentation.

---

### Post by zircon214 on 2010-01-21
I use the following to seed linux distro torrents if I've deleted the original iso, but it can be used to just verify a good burn.

Unmount and copy the disk to a file.

```
sudo umount /dev/scd0
dd if=/dev/scd0 of=ubuntu.iso
```Use "ls -l" to obtain the size of the original iso and the iso you just created. If they're the same size, great, use md5sum to verify the burn. But, if you notice the new iso is slightly larger than the original you'll need to shave off the end of the file before using md5sum on it.

```
split -b ORIGINAL-ISO-SIZE ubuntu.iso
```This will create two new files xaa and xab. Use md5sum on xaa to verify the burn. (The xab file will be nothing but zeros. Use a hex editor to open it if you're curious.)

---

### Post by Leppie on 2010-01-21
to check a cd:
```
md5sum /dev/cdrom
```

---

