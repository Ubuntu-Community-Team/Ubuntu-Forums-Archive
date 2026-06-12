---
title: "WinXP truncates long filenames saved on Ubu CD"
date: 2011-04-01
forum: General Help
---

### Post by mark bower on 2011-04-01
I have created a CD-Rom with pictures with long file names, up to 120 characters, using Brasero disk burner supplied with Ubu 10.10.  I need Win XP to accept the long file names from the CD made in Ubuntu without truncating them.  The WinXP HD is formatted NTFS.

1) When I look at the CD made in Ubuntu with long file names,in Win XP, it shows the file names only in the 8.3 (DOS) format.  When I open in Irfanview, the file names are also truncated. 

2) When I email the pictures (with long file names) from Ubuntu and accept in XP, the photo file names (long) are seen unaltered.  They can be stored, managed and used by viewing applications with the long file names.

note:  in XP, a short file name for a photo can be made to be very long, say 150 characters, and there seems to be no problem in manipulating it or viewing it.

What needs to be done for XP to accept the long file names that are on the CD-ROM produced in Ubuntu.

mark bower

---

### Post by mark bower on 2011-04-01
bump

---

### Post by mark bower on 2011-04-02
bump

---

### Post by Mark Phelps on 2011-04-02
First of all, quit bumping over and over -- it's rude!

Second, the filename truncation is usually determined by the format in which you burn the CD.  If you choose ISO by default, it will truncate to 8.3.

Choose a format that allows long filenames and you should be OK.  I think you could do that with UDF.

---

### Post by mark bower on 2011-04-02
i believe you may not have understood my post.  the CD burns as intended via Brasero in Ubuntu; the file names are long as viewed in Ubuntu. the problem is on the receiving end in WinXP.  WinXP only sees the files as 8.3 on the CD, and when copied to the XP desktop.  Brasero has an option to truncate to about 62 characters; XP can see the 62 characters, but that does not satisfy the need to retain the original file name (long version) in XP.

one workaround solution is to zip the files, then unpack in XP or Win7 - it works.  but not tidy.  i am hoping there is a trick to get XP (and probably needed for Win7) to accept the longer file names off of an uncompressed CD.

[bumping is definitely justified in order to dynamically obtain a response. scan older posts looking for help, and see the "buried" and stale posts with no response.  the issue is what would be an appropriate interval to bump if responses are not forth coming?  i have not seen a policy on this? so given no policy, the discretion will remain with the urgency of the poster.  generally i go for once per 24hr or so, but accelerated on this topic for urgency reasons]

mark bower

---

### Post by mark bower on 2011-04-03
bump for response

---

### Post by RedRat on 2011-04-03
I have had nothing but headachs and coasters from Brasero, I would suggest you try GnomeBaker instead. 

Further, try looking at your settings for burning data CDs/DVDs and before you burn make sure you select the filesystem you wish to use: Joilet and Rock Ridge, select both of these. 

I think what you are doing is using the default in Brasero which I think is ISO as mentioned. 

I gave up on Brasero years ago only use GnomeBaker and also K3b, take you choice.

---

### Post by mark bower on 2011-04-04
@ RedRat

o.k., i may be a little dense on this. it sounds like what you are saying is that even though Brasero burns the long filenames just fine, it records them in a form which XP and possibly Win7 do not like.  but if i record using GnomeBaker or K3b, i will not only have the same long file names to use in Ubuntu, but also XP and I guess Win7 will now accept the long file names off of CD?  would this be correct?

if so, time for me to play with the two apps you cite.

and again, just to be clear, i can pass file names up to 62 characters from Ubu to XP using a choice in Brasero.  problem is that 62 characters is not enuf.

mark bower

---

### Post by RedRat on 2011-04-04
> **mark bower said:**
> @ RedRat

o.k., i may be a little dense on this. it sounds like what you are saying is that even though Brasero burns the long filenames just fine, it records them in a form which XP and possibly Win7 do not like.  but if i record using GnomeBaker or K3b, i will not only have the same long file names to use in Ubuntu, but also XP and I guess Win7 will now accept the long file names off of CD?  would this be correct?

if so, time for me to play with the two apps you cite.

and again, just to be clear, i can pass file names up to 62 characters from Ubu to XP using a choice in Brasero.  problem is that 62 characters is not enuf.

mark bower
I had this same problem several years ago when I switched to Ubuntu and fought Brasero. Again, it is the file system you choose as I mentioned in my post, the Joliet and Rock Ridge system. If I recall correctly, Ubuntu and Linux support file names of at least 128 characters, both upper and lower case. I think Windows since Win98 support 256 characters but they are all considered uppercase. 

I too observed that 8.3 thing until I changed the filesystem. Now I don't use Win7, but have seen my current CD/DVD data disks on XP and Vista and they appear to be long file names. I don't tend to use file names that long, i.e., 60+ characters, I prefer shorter ones.

Why not give GnomeBaker or K3b a try and set the filesystem as I suggested.

---

### Post by mark bower on 2011-04-04
i will try the apps within a few days.  return and i will have posted what i have learned/can do.  

thanks
mark bower

---

### Post by mark bower on 2011-04-05
o.k. - this is what i know

GnomeBaker and K3b will store long file names not sure how long; i burned using 104 in my test, ie, "100" description plus ".jpg" for a total of 104 characters.  K3b has choice for Linux + Windows file storing (which i choose), and GnomeBaker i strictly used as installed.

As seen in Ubuntu: K3b (using the Linux+Windows option), the file description was reduced by 1, for a total of 99 chars +.jpg; GnomeBaker the file length remained unchanged as 100 chars +.jpg

As seen by XP off of each of the CDs burned above: K3b file length appeared the same as in Ubuntu, 99+.jpg; GnomeBaker the file length was truncated from the end such that the "g" was dropped to produce a total file length of 103 characters, ie, 100+.jp. 

so, this is a vast improvement vs a 8.3 result when looking at the CDs in XP.  i shortened my longest file name so that it meets the no more than 99 char (103) max character length.

two additional points:  1) if i want a longer file name, i can always revert to the ZIP file method of transfer, 2) the reason for long file names is photo archiving where fulls names, multiple persons in picture, place where picture taken, activity etc may be used.  in some cases, we are scanning cira 1850 family B&Ws.

@ RedRat - you have led me to what appears to be a final and very workable solution, ie use of GnomeBaker or K3b.  Thanks.

mark bower

---

### Post by mark bower on 2011-04-05
o.k. - this is what i know

GnomeBaker and K3b will store long file names not sure how long; i burned using 104 in my test, ie, "100" description plus ".jpg" for a total of 104 characters.  K3b has choice for Linux + Windows file storing (which i choose), and GnomeBaker i strictly used as installed.

As seen in Ubuntu: K3b (using the Linux+Windows option), the file description was truncated by 1, for a total of 99 chars +.jpg; GnomeBaker the file length remained unchanged as 100 chars +.jpg

As seen by XP off of each of the CDs burned above: K3b file length was the same as seen in Ubuntu, 99+.jpg; GnomeBaker the file length was truncated from the end such that the "g" was dropped to produce a total file length of 103 characters, ie, 100+.jp. 

so, this is a vast improvement vs a 8.3 result when looking at the CDs in XP.  i shortened my longest file name so that it meets the no more than 99 char (103) max character length.

two additional points:  1) if i want a longer description, longer than 99, i can always revert to the ZIP file method of transfer, 2) the reason for long file names is photo archiving where fulls names, multiple persons in picture, place where picture taken, activity etc may be used.  in some cases, we are scanning cira 1850 family B&Ws.

@ RedRat - you have led me to what appears to be a final and very workable solution, ie use of GnomeBaker or K3b.  Thanks.

mark bower

---

### Post by RedRat on 2011-04-05
> **mark bower said:**
> o.k. - this is what i know

GnomeBaker and K3b will store long file names not sure how long; i burned using 104 in my test, ie, "100" description plus ".jpg" for a total of 104 characters.  K3b has choice for Linux + Windows file storing (which i choose), and GnomeBaker i strictly used as installed.

As seen in Ubuntu: K3b (using the Linux+Windows option), the file description was truncated by 1, for a total of 99 chars +.jpg; GnomeBaker the file length remained unchanged as 100 chars +.jpg

As seen by XP off of each of the CDs burned above: K3b file length was the same as seen in Ubuntu, 99+.jpg; GnomeBaker the file length was truncated from the end such that the "g" was dropped to produce a total file length of 103 characters, ie, 100+.jp. 

so, this is a vast improvement vs a 8.3 result when looking at the CDs in XP.  i shortened my longest file name so that it meets the no more than 99 char (103) max character length.

two additional points:  1) if i want a longer description, longer than 99, i can always revert to the ZIP file method of transfer, 2) the reason for long file names is photo archiving where fulls names, multiple persons in picture, place where picture taken, activity etc may be used.  in some cases, we are scanning cira 1850 family B&Ws.

@ RedRat - you have led me to what appears to be a final and very workable solution, ie use of GnomeBaker or K3b.  Thanks.

mark bower
Thanks Mark, glad I was able to help. I have found BnomeBaker to be much, much better. Interesting to hear that about K3b, I don't use such long file names so have not actually run into the problem.

---

