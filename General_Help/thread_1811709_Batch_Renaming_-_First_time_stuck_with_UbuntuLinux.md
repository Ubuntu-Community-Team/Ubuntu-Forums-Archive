---
title: "Batch Renaming - First time stuck with Ubuntu/Linux"
date: 2011-07-25
forum: General Help
---

### Post by dwlima on 2011-07-25
SOLVED

I have thousands of photos, and need to rename them in the following format:
date created (space) time created(_x).jpg

date: dd-MMM-yyyy (01-Sept-2002) 
time: HH.mm.ss (14.05.20)

If there are distinct date&time combinations, then just the date created & time created (e.g., 01-Sept-2002 14.05.20.jpg) would the the file name. If there happened to be 2 pics taken at the same date/time, then it would be 01-Sept-2002 14.05.20_1.jpg and 01-Sept-2002 14.05.20_2.jpg.

In the past to accomplish this, I used winsome renamer in windows. I renamed all the pics to _1 incrementing by 1 (_1, _2, _3, etc). I used the prefix date and time section to add the date and time with the appropriate "-"s and "."s. I was left with some _x even when unnecessary (ie, distinct file names upon creation), but that was acceptable although not ideal.

I have tried Krename, GPRename, pyRename and Thunor - thus, only GUIs so far. Aside from the issue of adding the "-"s and "."s to the filenmame, they obviously use "Photo.DateTimeOriginal" which seems to only set the date format as yyyy:mm:dd (2002-09-01) in these linux softwares. 

I also tried using Winsome Renamer with WINE (did not work) and the option left would be to move all the photos to a VM running Windows and move them all back and do this going forward...not such a nice solution.

If anyone can help, I would really appreciate it. 

Newbie
Dwlima

---

### Post by Jacks0n on 2011-07-25
Hm, interesting problem!

I don't know about a program to do this for you, but here's a quick Python script I wrote. I put extra comments in so you can see what it does out of interest.

This *should* work ;-)

Save the script to your desktop, and make it executable (right click, properties, then tick make executable) and change where it says...

```
directory = '.'
```

To the path of the directory where you want to rename your files.

Currently it does a dry run and tells you what it will do. If you want it to actually rename files, just change...

```
# os.rename(filepath, newFilename)
```

to

```
os.rename(filepath, newFilename)
```

---

### Post by dwlima on 2011-07-25
Thank you Jacks0n for your quick response. After being a Microsoft zombie for 20+ years, I am thinking of converting my other PC to Linux-only. The ideology, the amazing generosity of the linux users' time, and the fact that it is simply a much better OS are all prominent reasons. 

I wish I could more easily modify your script, but I need your help to fix it. Here are the problems. 1) The date is second, and I wanted to rename the file with the date first. I am assuming that is just a switching of the order on newFilename = ...[...timeStr, dateStr] 2) More importantly, the date and time are wrong. As for the date, there is something wrong with "datetime.date.fromtimestamp(unixCreation)". Each pic has several dates, such as date created, date modified, date accessed, as you know. From exiv2, I need "[exifExif.Photo.DateTimeOriginal]" as that appears to have both proper date and time for when these pics were truly created. 

If you could help me with this last part, I would be grateful. 

DWlima

---

### Post by Jacks0n on 2011-07-26
No problem :-). Ah I see, yeah Linux is certainly different that's for sure. I suppose I like the flexibility of being able to configure it to my liking, and do what I want with the system.

I had a play around with the script, and used a Python module called "pyexiv2" for the exif data. It will also handle situations if there is no exif data available. You will probably have to install pyexiv2. Just type the following in the console/terminal.

```
sudo apt-get install python-pyexiv2
```

Also the new script attached is live! So you may want to test it out on a small folder first ;-). Good luck, let me know if it works!

---

### Post by fdrake on 2011-07-26
i did something like that but in bash instead. you need to place it in the directory of the pics.make executable (chmod +x rnm_photo.sh)and run it. You need to run in sudo since it  needs to download a program jhead (to collect image infos),It doesn't matter if you have a mix of different files, the script will  recognize the image files from the others.


edit: I forgot to Un-comment line #7 that's why the script wasn't working. Now should be fine.

---

### Post by dwlima on 2011-07-26
Jacks0n: That worked like a charm. Truly, thanks a lot! I added "print newFilename" and commented out the rename so I can see the results in Terminal. I wish I could write such a script, but my programming days are 25 years behind me :) 


Fdrake: This is what happened after running your script. btw, you don't need to spend any more time on this since I have a working script. If you do, I will run it and let you know how it works out.
_______________________Installing *jhead*_________________________

#################################################################
____________Creating Folder *IMG* for re-named filesw______________

##################################################################
Testing if file 06-Sep-2002 20.47.45.JPG is an image file...
The file is an image. 
 Renaming image in IMG folder: 06-Sep-2002 20.47.45.JPG =================>>> 1 
./rnm_photo.sh: line 25: jhead: command not found
./rnm_photo.sh: line 26: jhead: command not found
./rnm_photo.sh: line 27: jhead: command not found
./rnm_photo.sh: line 28: jhead: command not found
./rnm_photo.sh: line 29: jhead: command not found
./rnm_photo.sh: line 30: jhead: command not found
-- ..1.jpg
rm: cannot remove `./IMG/06-Sep-2002 20.47.45.JPG': No such file or directory

##################################################################
Testing if file IMG is an image file...
file IMG is not an image!
##################################################################
Testing if file rnm_photo.sh is an image file...
file rnm_photo.sh is not an image!
##################################################################

 Total number of images found: 1 
 All your images have been renemed and saved to ./IMG folder, Do you want to open the folder now? y or n 
y

***The result was the file was renamed to --..1.jpg***

---

### Post by dwlima on 2011-07-26
Jacks0n:

I finished my photos and am now working on my videos. I did not realize that exiv2 was exclusively for jpeg files. For these avi files, I need to use "[creationdate]" and I don't see "[creationtime]" in Krename, although I am sure it must exist. Could you please help me with this last issue - it would complete my media renaming. tia.

btw, I want to use the same naming convention as for the pics.

---

