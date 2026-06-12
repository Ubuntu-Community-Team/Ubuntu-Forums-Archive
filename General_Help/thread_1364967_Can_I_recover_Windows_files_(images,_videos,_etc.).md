---
title: "Can I recover Windows files (images, videos, etc.) after installing Ubuntu?"
date: 2009-12-26
forum: General Help
---

### Post by ray023 on 2009-12-26
I had a friend who's Windows OS got hosed. I advised him to download and boot a Live CD version of Ubuntu so that he could try and recover his important files. (pictures, video, etc.)

I thought I was pretty clear with my instructions, but today he called me and said "...so I installed Ubuntu onto the hard drive and I can't find my files."  :confused:

I told him to leave the laptop off and bring it to work with him this week.

I'm not sure what he's done yet, but I know Ubuntu loads without the CD and he said it does not dual-boot.

If he went through Ubuntu's full install process, is there a way to recover any files that may not have yet been overwritten?

AFAIK, everything is on a single partition.

---

### Post by oldos2er on 2009-12-26
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by webbdawg on 2009-12-26
I have full access to my Windows folders from my Kubuntu.

The windows premsissions are irrelevant too, which is great.

Did you install as a dual boot??

---

### Post by akand074 on 2009-12-26
Well that depends what he did. If he installed Ubuntu on a separate partition then all his files would be easily accessible from ubuntu by mounting the Windows partition and copying all the files he needs into the ubuntu partition. If he reformatted the Windows partition and used it to install ubuntu, then all the files were removed and I don't think they are recoverable. I would boot into his Ubuntu partition and see if you can find his windows partition, if not it has probably been formatted and used otherwise ubuntu would be able to find it. 

Anyways if he didn't know what he was doing, chances are he used to automatic install instead of the manual install and it automatically created the ubuntu and swap partition with unused space on the hard drive. If thats the case it should be fine, otherwise I don't think it can be recovered.

---

### Post by Leppie on 2009-12-27
if your friend did install ubuntu over his windows, changes are that a good amount of his documents have not yet been overwritten. standard windows installs usually occupy much more disk space than ubuntu installs. obviously this depends on what is installed on both os's as well.
not sure if he could recover the files as windows is using ntfs and ubuntu ext4, but give testdisk a try.

---

### Post by ray023 on 2009-12-27
Ok, some of that news is somewhat comforting.

I'm hoping that maybe the automatic install is what he used.

I won't know till around Tues. of this week.

I will post what I find.

Guys...ty for all the responses!!!

---

### Post by ray023 on 2009-12-31
Mega-props to **oldos2er**!!!!!!

After getting the laptop, I booted the Ubuntu LiveCD and looked at the partitions.  Oh yes, the hard drive had been completely formatted for Ubuntu.  No visible sign of Windows what-so-ever.

So I went to the link **oldos2er **recommended, downloaded the app and ran [PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec") (whose name, by the way, doesn't quite encompass the app's ability as it can recover all kinds of files).

Since this was just a rescue mission for jpgs, I narrowed the search down to just that type of file and, 10 hours later, I had over 14,000 images recovered on a thumb drive. 

I actually wanted to recover to a network folder, but I was having Samba issues (it had been a while since I fooled with Samba).  I found [this link]("http://ubuntuforums.org/showthread.php?t=1169149") which gave a lot of troubleshooting steps, but I still had no luck.  No matter, everything I needed fit on my 4GB thumbdrive (most of those 14,000 came from Internet Cache).

The important files were there.

And so, as a side, non-technical note, I want you guys to know that this was actually for the guy's girlfriend whose father recently passed away.  She had some pictures of them on there and I was able to recover them thanks to your help.

Hope you have a Happy New Year!

---

