---
title: "On hard drive, find all JPG photos taken on August 26"
date: 2009-09-05
forum: General Help
---

### Post by hanzj on 2009-09-05
Hello,
I downloaded/copied some pictures from my digital camera to my ubuntu computer. The problem is, I can't seem to find these photos. I don't know their exact filenames, as they are the filenames created by the camera. All I know is:


[LIST]
[*]they start with a capital P
[*]they end in .JPG
[*]the photos were taken on August 26, 2009
[/LIST]

Thank you.

---

### Post by ad_267 on 2009-09-05
Assuming they're somewhere in your home directory, go to applications - accessories - terminal and run:

```
find -iname "*.jpg" -mtime -4
```

To search everywhere within your root directory, put a / after find:
```
find / -iname "*.jpg" -mtime -4
```

---

### Post by kyle6513 on 2009-09-05
take a photo with your camera and note the file name, it might have something to do with the date then input the numbers of the past three days into 3 different searches and that should work!
hope you can find them

---

### Post by hanzj on 2009-09-05
thanks. can't seem to find them. do your commands go through the pictures' "access date"? Or pictures' "modified date"?

Coz I think it looks at modified date, which is the date I snapped the photos. But I need the later "accessed date". How can we change the find command to comb through  "accessed date"?

Thanks.

---

### Post by hanzj on 2009-09-05
right. they all start with a Capital P.

---

### Post by ad_267 on 2009-09-05
You're right, it should be "-atime" for accessed. I also had the number wrong the first time, you will want to use "-4", not "3" (I edited my post but you might have missed that). That will give you anything accessed less than 4*24 hours ago.

---

### Post by hanzj on 2009-09-05
Or can I have FIND comb through "Date Taken" info (I guess this is in the EXIF data)?

---

### Post by ad_267 on 2009-09-05
> **hanzj said:**
> Or can I have FIND comb through "Date Taken" info (I guess this is in the EXIF data)?

Possibly, but I wouldn't know how to do that. You can have a look at the find man page (man find) and see if there's any other options that will help, but using -atime -4 should work. You might want to use the -L option to follow symbolic links if you have directories that are linked from other partitions.

---

### Post by rockstarrem on 2009-09-05
Just adding in my two cents here, this is probably really un-useful but if it is then your welcome :P.

```

locate *.jpg

```

If you have a lot of .jpg's then yeah, sorry haha.

---

### Post by swoody on 2009-09-05
> **hanzj said:**
> [LIST]
[*]they start with a capital P
[*]they end in .JPG
[/LIST]


The find command should be what you need here. However, do be careful in your search terms. My camera uploads pics as .JPG files, not .jpg files. There is a difference in Linux. Keep an eye on your capitalization when you run the search commands above, and you it should help you avoid mistakes :)

---

### Post by ad_267 on 2009-09-05
> **swoody said:**
> The find command should be what you need here. However, do be careful in your search terms. My camera uploads pics as .JPG files, not .jpg files. There is a difference in Linux. Keep an eye on your capitalization when you run the search commands above, and you it should help you avoid mistakes :)

Yeah, the "-iname" option instead of "-name" takes care of that when using find. :)

---

### Post by hanzj on 2009-09-05
Yes, 
locate *.jpg would be unhelpful, because I have a lot of JPGs

---

### Post by LewRockwell on 2009-09-05
> **kyle6513 said:**
> take a photo with your camera and note the file name, it might have something to do with the date then input the numbers of the past three days into 3 different searches and that should work!
hope you can find them

download another photo to the computer and note where it's saved to?...maybe?...perhaps?

.

---

### Post by ad_267 on 2009-09-05
The find command should work if they're there. Try pushing the time limit out a bit and add the "beginning with P" part. You could also search for a modification date within a certain interval. Eg for less than 6 days but greater than 2:
```
find -L -iname "P*.jpg" -mtime -6 -mtime +2
```
Or an access date:
```
find -L -iname "P*.jpg" -atime -6 -atime +2
```

Also read the man page and try other options that might help. If it doesn't find anything I'd be inclined to think you may never have transferred them, or they were accidentally deleted.

---

### Post by hanzj on 2009-09-05
I updated my original post with another criterion.

The photos were all taken on August 26. Is there a way to search using only this one criterion?

---

### Post by hanzj on 2009-09-05
Hello,
I seem to have misplaced some of my jPGs transferred from digital camera to  the ubuntu hard drive. I took pictures on August 26, 2009. I transferred them on an unknown date/day.

How could I search my hard drive for all photographs that were taken on August 26. They all start with Capital P. They all end in Capital .JPG.

Thanks.

---

### Post by arkticcool on 2009-09-05
Just type in:

```
find -name P*.JPG
```

Into terminal

---

### Post by Gen2ly on 2009-09-05
Just to let you know 'find' better:

```
find /directory/to/start/in -name P*.JPG
```

Otherwise arkticcool's command will start find in the current directory.

---

### Post by Gen2ly on 2009-09-05
Ugh, cross-post:

[http://ubuntuforums.org/showthread.php?t=1258949](http://ubuntuforums.org/showthread.php?t=1258949)

---

### Post by Johnny B on 2009-09-05
find /home -iname "P*.jpg" -mtime 10

10 meaning all files modified exactly 10 days ago

---

### Post by kaibob on 2009-09-06
> **hanzj said:**
> Or can I have FIND comb through "Date Taken" info (I guess this is in the EXIF data)?

You can get the exif timestamp with the exiv2 utility. For example:

> $ exiv2 sample.jpg
File name       : sample.jpg
File size       : 2692270 Bytes
MIME type       : image/jpeg
Image size      : 3072 x 2304
Camera make     : Canon
Camera model    : Canon PowerShot SD1000
Image timestamp : 2008:09:23 13:14:18
Image number    : 100-0045
Exposure time   : 1/400 s
Aperture        : F2.8
Exposure bias   : 0
Flash           : No, auto
Flash bias      : 0 EV
Focal length    : 5.8 mm
Subject distance: 559
ISO speed       : 80
Exposure mode   : Easy shooting (Auto)
Metering mode   : Multi-segment
Macro mode      : Off
Image quality   : Superfine
Exif Resolution : 3072 x 2304
White balance   : Auto
Thumbnail       : image/jpeg, 5094 Bytes
Copyright       : 
Exif comment    : 

I briefly tried the following shell script, and it appears to do what you want:

```
#!/bin/bash

find -name 'P*.JPG' -type f 2>/dev/null | while read file ; do
   exiv2 pr "$file" | grep 2009:08:26 && echo "$file" 
done
```

You can use this by entering the following as one long command line in a terminal window:

```
find -name 'P*.JPG' -type f 2>/dev/null | while read file ; do exiv2 pr "$file" | grep 2009:08:26 && echo "$file" ; done
```

---

### Post by hanzj on 2009-09-07
kaibob,
thanks for your post. I did the command and didn't find the pics. I guess I accidentally deleted them or never moved them over to my hard drive.

---

