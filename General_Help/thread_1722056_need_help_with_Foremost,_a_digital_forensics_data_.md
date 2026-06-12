---
title: "need help with Foremost, a digital forensics data recovery tool"
date: 2011-04-05
forum: General Help
---

### Post by bitbomb on 2011-04-05
I'm trying to learn how to use foremost, a data recovery tool.  I thought a nice place to start would be by attempting to recover a file from a test image.  The [foremost website]("http://foremost.sourceforge.net/") links to [this site]("http://dftt.sourceforge.net/") which has a [FAT Undelete Test #1]("http://dftt.sourceforge.net/test6/index.html") challenge.  The challenge is to recover files from a 6 MB FAT disk image.  I tried running this command...

foremost -t all -i /home/<user>/Desktop/6mb.img -o /home/<user>/Desktop/output

but all I got was a folder with an audit.txt file in it.  What am I doing wrong?

---

### Post by oldfred on 2011-04-05
I used photorec, but not foremost.

See these links for more info:

[http://www.howtoforge.com/recover-deleted-files-with-foremost](http://www.howtoforge.com/recover-deleted-files-with-foremost)
[http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html](http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html)

---

### Post by bitbomb on 2011-04-05
Thank you for the links.  I will give photorec a shot.  I did some reading and found that I need to uncomment the file types that are listed in the foremost.conf file.  In addition, I need to use "sudo foremost....." instead of "foremost....".  However, I still cannot recover any data from FAT Undelete Test #1 image using foremost.  

I tried using testdisk and I can see all the deleted data on the FAT Undelete Test #1 and recover most of it.  However, no matter what I try, foremost does not work.  I would have thought foremost to be suited to this task better than testdisk.

---

### Post by bitbomb on 2011-04-06
Okay, been doing a lot of testing with these tools...

I have tried the following...

Photorec
magicrescue
scalpel
foremost
testdisk

For my test I took a FAT32 formated 4GB flash drive and put a 800 byte text file, a 70 KB jpg file, a 50 MB wmv file, and a 150 MB avi file.  Then I deleted them and made a image using dcfldd.  I tested the following applications using the following commands...

**magicrescue**
sudo magicrescue -r avi -r jpeg-jfif -r jpeg-exif -d /home/"user"/Desktop/output /home/"user"/Desktop/dcfl.dd
Notes:
There was no recipe for text files or wmv files, magicrescue won't recover these.

**scalpel**
sudo scalpel -o /home/"user"/Desktop/output /home/"user"/Desktop/dcfl.dd
Notes:
The jpg, txt, and avi options were uncommented in the scalpel.conf file.  The scalpel.conf file had no entry for wmv files, scalpel won't recover these.

**foremost**
sudo foremost -t all -i /home/"user"/Desktop/dcfl.dd -o /home/"user"/Desktop/output
Notes:
The jpg, txt, and avi options were uncommented in the foremost.conf file.  I tried to uncomment the wmv section but foremost wouldn't run if I did this.  It kept giving me a "segmentation fault" error.  Yet again, wmv files won't be recovered.

**testdisk**
testdisk /home/"user"/Desktop/dcfl.dd
non partitioned media, analyze, quick search, 

**photorec**
photorec /home/"user"/Desktop/dcfl.dd
non paritioned media, search, other


Magicrescue recovered the jpg file, it did not recover the avi.  Text and wmv files were not recovered, which was expected.
Scalpel recovered the jpg file and 47.7 MB of the avi file, it did not recover the text file.  Wmv file was not recovered, which was expected.
Foremost did not recover any of the files.
Testdisk successfully listed and recovered all files
Photorec successuflly recovered all files

**Conclusions:**

I think that magicrescue, foremost, and scalpel work differently than testdisk and photorec.  Magicrescue, foremost, and scalpel seem to be actual "data carvers".  In other words, these application don't use the file system of the image, they just look for the header and footer of a file and attempt to recover the data in between that.  Still, I'm not sure why they did not work so well in this test.  Their performance seems to be dependant on the magic numbers listed in the config or recipe files.

On the other hand photorec and testdisk seem to be well suited to recovering data from a file system that is still "intact".  These may be better choices for recovering data from disk images where the file has been accidentally deleted.

I will test these using the FAT Undelete test 1 sometime in the near future.

---

### Post by oldfred on 2011-04-06
For some reason on my system I lost two folders. I used photorec to recover data and I think it did not just recover the missing folders but all files on the drive. 

One of several files I really wanted back is some of my notes on what works and links to fixing grub issues. I am copying data & updating almost daily and it is just a text file. I had a backup but it was several months old. (Do as I say do not do as I do, or backup often)

Photorec found that text file from every time I saved it. I had many copies and am not sure I every found the last saved version. Since I had lots of other text files and many other files I ended up doing a lot of grepping and file comparing and got most of the data back. But since drive has lots of space it was interesting to note that the same file exists many times and was not just overwritten each time.

---

### Post by bitbomb on 2011-04-06
Well, it looks like photorec might be the app of choice for accidentally deleted files.  It seems that photorec is also a "data carver" since it seems to ignore the file system also ([see description here]("http://www.cgsecurity.org/wiki/PhotoRec")).  As far as why it worked so much better than the other data carvers, I have no idea.

---

