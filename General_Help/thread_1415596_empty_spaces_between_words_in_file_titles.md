---
title: "empty spaces between words in file titles"
date: 2010-02-25
forum: General Help
---

### Post by joham34 on 2010-02-25
hello everybody 
I am quite new to Linux but am impressed from its beauty and strength 
What I want to ask, is 
I have a large archive with openoffice docs. I name the docs as e.g
johnsmith 230465 good man , where johnsmith the name , 230465 birthdate and good man a characteristic for the particular man. 
When I open my archive , it takes some time , about  seconds to be read. May be a reason is the empty spaces in the name of the doc? Should it be better to name it like : 
johnsmith_230465_good_man? 
And what kind of command should I try in the terminal to rename all my archives?
I have Jaunty Jackalope 
Thanks in advance

---

### Post by rnerwein on 2010-02-25
hi
if think it's better to work without spaces in filenames in unix/linux systems.

to change your filenames use following command in your directory:
rename 's/\ * /_/g' fi*
this give you if a filename is e.g. is: field1 field2     field3  field end
as a result: field1[COLOR=Red]_[/COLOR]field2[COLOR=Red]_[/COLOR]field3[COLOR=Red]_[/COLOR]field[COLOR=Red]_[/COLOR]end

all spaces are converted to one singel [COLOR=Red]_[/COLOR] 

please test it out with a couple of files to see if this is the result you want to get.
ciao

if you got very much files in one directory it will take some time to "stat" them all. better is for future to structure your collections e.g.   music_folder contains classic_folder, funk_folder, soul_folder and so on. this is a better way to speed up ( and for your brain too ) the access.

---

### Post by stinkeye on 2010-02-25
I tried 
```
rename 's/\ * /_/g' fi*
```
and nothing changed.

---

### Post by joham34 on 2010-02-25
Dear Rnerwein thanks for the immediate reply 
I tried rename 's/\ * /_/g' fi* but nothing changed . Any idea ?

---

### Post by PoHandle on 2010-02-25
With regards to OpenOffice taking time to open your documents, there was a tip I found somewhere (I forget where) that suggested tweaking some of the memory settings in OpenOffice.

I have 2GB of RAM, and my memory settings (Tools > Options > Memory) are as follows:

[LIST]
[*]Number of steps: 30
[*]Use for OpenOffice.org: 128 MB
[*]Memory per object: 10 MB
[*]Remove from memory after: 00:10 hh:mm
[*]Number of objects: 20
[/LIST]
I left the systray quickstarter option unchecked, but if you do check it, OpenOffice should load faster.

As for the mass renaming to replace blank spaces, make sure all your documents are in the same directory, then:

Open a terminal and go to that directory
```
cd /*path-to*/*your-directory*
```
where you would enter the actual path to that directory.

List your files
```
ls
```

Rename them by replacing all spaces with underscores
```
rename "s/ /_/g" *.**odt**
```
You can replace .odt with whatever file extension you want (.doc, .txt, etc.)

---

### Post by joham34 on 2010-02-26
> **PoHandle said:**
> With regards to OpenOffice taking time to open your documents, there was a tip I found somewhere (I forget where) that suggested tweaking some of the memory settings in OpenOffice.

I have 2GB of RAM, and my memory settings (Tools > Options > Memory) are as follows:

[LIST]
[*]Number of steps: 30
[*]Use for OpenOffice.org: 128 MB
[*]Memory per object: 10 MB
[*]Remove from memory after: 00:10 hh:mm
[*]Number of objects: 20
[/LIST]
I left the systray quickstarter option unchecked, but if you do check it, OpenOffice should load faster.

As for the mass renaming to replace blank spaces, make sure all your documents are in the same directory, then:

Open a terminal and go to that directory
```
cd /*path-to*/*your-directory*
```where you would enter the actual path to that directory.

List your files
```
ls
```Rename them by replacing all spaces with underscores
```
rename "s/ /_/g" *.**odt**
```You can replace .odt with whatever file extension you want (.doc, .txt, etc.)


Thanks, it worked ! Blank spaces in my filenames are substituted by underscore. 
As for Open office, it opens my docs fast, its the browsing of the folder with my files that is somewhat slow (I think its slightly faster now but am not sure).  My archive is in a FAT32 formatted flash disc. May be I should try to format it to ext3 or ext4?

---

### Post by PoHandle on 2010-02-26
> **joham34 said:**
> My archive is in a FAT32 formatted flash disc. May be I should try to format it to ext3 or ext4?

EXT3 (and 4) certainly has faster read/write speeds than FAT32, and formatting your flash drive to EXT3 will most likely increase browsing speed.  However if you plan to access the data on your drive using an operating system other than Linux, it is recommended that you stick with FAT32.  Windows and OSX will only be able to mount EXT3 partitions using special software.

---

### Post by falconindy on 2010-02-26
> **PoHandle said:**
> EXT3 (and 4) certainly has faster read/write speeds than FAT32, and formatting your flash drive to EXT3 will most likely increase browsing speed.  However if you plan to access the data on your drive using an operating system other than Linux, it is recommended that you stick with FAT32.  Windows and OSX will only be able to mount EXT3 partitions using special software.
NTFS is a better option. FAT32 is old and crusty.

---

### Post by rnerwein on 2010-02-27
> **joham34 said:**
> Dear Rnerwein thanks for the immediate reply 
I tried rename 's/\ * /_/g' fi* but nothing changed . Any idea ?

hi
don't use your ! filnames not "fi*".

rename 's/\ * /_/g' *.bla  ( or what endung you got ) note between /\ and * and / is always one space.
this command will cause that even when there are more spaces between the part of the filename will be replaced by one underscore and not each space by an underscore.
ciao

---

