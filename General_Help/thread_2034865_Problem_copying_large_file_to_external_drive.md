---
title: "Problem copying large file to external drive"
date: 2012-07-29
forum: General Help
---

### Post by houseworkshy on 2012-07-29
I'm currently duel booting ubuntu 10.04 with Mepris, they have a hard drive each.  I've downloaded a file for an offline windows using friend.  It's called kwiks and is the entire wikipedia without pictures, this is it's homepage [http://www.kiwix.org/index.php/Main_Page](http://www.kiwix.org/index.php/Main_Page).  It's a big file at 17.8 GB and is already compressed so I doubt it could be shrunk further.  It came in ok but is too large for a dvd or any stick either of us have so I've been trying to put in on an external usb hard drive so I can take it round.  

I can't get a copy onto the external hard drive from either side.  The Ubuntu side tried and tells me that it is too large to splice.  On looking at the external drive it has taken around 4gb of it but that's all.  I'm guessing that my ram+swap isn't big enough but don't actually know for sure.  Does anyone know of a way I can get this thing over.  And once there a way of putting onto my friends machine.  He's on a windows machine, Vista or 7,  probaby, because I know that he has to phone microsoft for unlock codes or reinstall once a month because he isn't online.

---

### Post by spjackson on 2012-07-29
4GB is the maximum filesize for a FAT32 formatted drive. [http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems) . I guess that the external drive is formatted as FAT32.

If you are wanting to write a large file that can be read on Vista or Windows 7 then you will first need to format the drive to NTFS. You can do this from Vista or Windows 7. If you want to do it from Ubuntu, I think gparted can do it, though I'm not sure whether it could format NTFS in 10.04.

---

### Post by Dr. C on 2012-07-29
This sounds like the limitations of FAT32 on the external drive. Gparted will format NTFS. The other was is to format Ex2 and use one of the Ex2 drivers for Windows. 

[www.fs-driver.org/]("www.fs-driver.org/")
[http://www.ext2fsd.com/]("http://www.ext2fsd.com/")
[http://www.howtoforge.com/access-linux-partitions-from-windows]("http://www.howtoforge.com/access-linux-partitions-from-windows")

---

### Post by houseworkshy on 2012-07-29
Thanks for that.  Yes the external drive is formated to FAT32, so that will be the problem.  It's got a lot of things I don't want to loose and the drive has to be universally compatable so unless I find a splitting 'spandisk-like' program, I will duck passing this file on. Thanks for your help

---

### Post by spjackson on 2012-07-30
I see you have marked this as solved, but you should be able to split your 17.8GB follows with something like this.
```

split -b 4GB -d bigfile bigfile-

```which will create 5 files
bigfile-x00
bigfile-x01
bigfile-x02
bigfile-x03
bigfile-x04

You can then join these back together on Windows with
```

copy/b bigfile-x00+bigfile-x01+bigfile-x02+bigfile-x03+bigfile-x04 bigfile

```This has worked for me in the past.

---

### Post by houseworkshy on 2012-07-31
That's really helpful thanks.  I'd only marked it as solved when informed it was a file system thing which I couldn't do much about.  Didn't think of looking for a command and had been browsing around for a program.  You may have saved me from posting again.  I'll try that and read up on split too.  The external hd is my main backup so being able to zip things large would be extreemly useful, especially for an archive.org addict like me.  Thanks again.

---

### Post by Cheesemill on 2012-07-31
You could also use zip to create a split archive:
```
zip -s 2g archive.zip <filename>
```
Would create the files archive.zip archive.z01 archive.z02 etc...
Each would be 2GB in size and can be easily extracted using Winzip on the Windows machine.

You don't even need to use the terminal, you can use the Archive Manager application that comes with Ubuntu. Just create a new archive, select .zip as the file format and choose your split size under 'Other Options'.

For both of these you may need to install zip first, I'm not sure if it comes with a standard installation:
```
sudo apt-get install zip
```

---

### Post by houseworkshy on 2012-07-31
The split command seems to have worked for part one of the operation and the file is now in FAT32 fitting segments though only x00 is shown as a zip and x01 to x04 show as unknown file types.  I won't know about how the slapping them on to the windows machine and sticking them together again goes until I call round and try, probably in a day or two.  Thanks for the know how, I'll be using that command a lot I think.

Thanks Cheesmill, that's another thing I didn't think of and a good idea.   Uncompressing ( that 17.8 gig is already a zip AND when unzipped reveals  yet another compressed format "ZIM" which may be unique to the project )  and recompressing but in segments.  I'll definately try that if part two of the split method, getting  it off the external and onto the windows machine, doesn't work.

---

### Post by Cheesemill on 2012-07-31
> **houseworkshy said:**
>   Uncompressing ( that 17.8 gig is already a zip AND when unzipped reveals  yet another compressed format "ZIM" which may be unique to the project )  and recompressing but in segments.

No need to uncompress it at all first, just create a split archive containing the zip file you already have. It won't decrease the overall size of the file any more but that's not the point of this operation.

---

### Post by houseworkshy on 2012-07-31
That's handy.  Therefore what I'll do is have both versions on the external ( there's room) so I can try both options on the spot.  Thanks.

---

