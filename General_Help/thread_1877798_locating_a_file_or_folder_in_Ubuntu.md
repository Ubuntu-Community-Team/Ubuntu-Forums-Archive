---
title: "locating a file or folder in Ubuntu"
date: 2011-11-08
forum: General Help
---

### Post by parts-man73 on 2011-11-08
I made the plunge headfirst into Ubuntu a couple months ago. I'm running the latest version  (11.10) and I'm loving it. 

There is a program I used to use under Windows, and sure enough, there is a version for Ubuntu,   Eagle Cad.   This question isn't Eagle CAD specific, but more about finding files in linux. 

I am having trouble finding a place to put my parts library files. in the options for the program there is a place to define paths. and I see the path for library files is

$EAGLEDIR/lbr

how do I find this folder in the file system to copy files to.  There are a number of libraries that come with Eagle, so I tried to search for the names of some of those libraries with Dash and Tracker's "desktop search" and it didn't find any files. I also poked around the "file system" looking for this "EAGLEDIR" and found nothing.  Do I just need to create the folder?  or where are these other library files that come stock with Eagle??? I'm stumped! 

Thanks in advance for the help!
Brian

---

### Post by An Sanct on 2011-11-08
The location is
```
/usr/share/eagle/lbr
```

It is also displayed, if you open one of the existing libraries, provided with eagle cad :)

---

### Post by 3rdalbum on 2011-11-08
When they describe a location as starting with a dollar sign ($) they're talking about a default location - so in your instance, $EAGLEDIR means "the folder where Eagle was installed". So $EAGLEDIR/lbr is the subdirectory lbr inside the folder where Eagle was installed.

It's a bit of Unix/Linux jargon I'm afraid, but you won't come across it too often I'm happy to say. If you do come across it again and you have difficulty finding the appropriate place, try looking in /usr/share.

---

### Post by parts-man73 on 2011-11-08
Excellent, found it!  I copied my library there, and I'm designing my new circuit board as we speak. I'm getting used to this, slow but sure. And as I said in the first post.  I'm loving it!  

I found that the files and folders in that area were locked to "root" only. I had to go in as root to give myself permission to access that folder. But now all is working nice!

---

### Post by parts-man73 on 2011-11-08
Also,  why did the desktop search not find any *.lbr files?  seems like it would have found the existing library files, and led me right to the proper folder.

---

### Post by dcstar on 2011-11-09
> **parts-man73 said:**
> I made the plunge headfirst into Ubuntu a couple months ago. I'm running the latest version  (11.10) and I'm loving it. 

There is a program I used to use under Windows, and sure enough, there is a version for Ubuntu,   Eagle Cad.   This question isn't Eagle CAD specific, but more about finding files in linux. 
........

```
man locate
```

---

### Post by parts-man73 on 2011-11-10
excellent.  Locate is a great tool! I typed Locate *.lbr and gave me a list of all those library files..  more than 1 way to skin a cat.  I'm getting used to linux, slow but sure

thanks everyone for helping this noobie out!

---

### Post by supershin on 2011-11-10
> **parts-man73 said:**
> Also,  why did the desktop search not find any *.lbr files?  seems like it would have found the existing library files, and led me right to the proper folder.

Could be that the search only checked the desktop folders and not in the filesystem.

Locate is an excellent tool to find files. You can also use the command find. type "man locate" in a terminal to see more info.

---

