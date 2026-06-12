---
title: "Managing downloaded files"
date: 2010-12-26
forum: General Help
---

### Post by afrodeity on 2010-12-26
I have a huge folder of downloaded files. Problem is, most of the file descriptions are useless. The files get downloaded over time because of slow-bandwidth, so I forget where I get them from or what they refer to.

I do not have any clue what the file names refer to and would have to manually google the file name, hoping to get a reference somewhere.

Surely there must be a way of keeping track of the **links to the files** when they are downloaded, so that I can backtrack to the reference material?

Any ideas appreciated.

---

### Post by afrodeity on 2010-12-26
I've filed it as a bug [https://bugs.launchpad.net/ubuntu/+bug/694453](https://bugs.launchpad.net/ubuntu/+bug/694453)

---

### Post by dino99 on 2010-12-26
file [option] file-list

Option

-f file
    When specified, the file command takes the list of file from the file specified after the -f parameter, you need to enter one name per line in that text file
-i
    Displays MIME file information, in MIME format
-L
    Shows the info of the files being symbolic linked and the link itself 
-z
    Classify the files contained by a compressed file

file can recognize more than 5.000 file types but it is not always accurate or exact.

---

### Post by mikewhatever on 2010-12-26
What application do you use for downloading? Does it have the features you want? If not, have you searched for one that does? For example, the download manager in Firefox provides both links and dates of the downloaded files.

---

### Post by afrodeity on 2010-12-26
> **mikewhatever said:**
> What application do you use for downloading? Does it have the features you want? If not, have you searched for one that does? For example, the download manager in Firefox provides both links and dates of the downloaded files.

Is that a firefox addon? Firefox 4 just has downloads ctrl shift Y? 

Chromium is a bit better, problem is I still end up with bunch of files in downloads, I guess this is a Nautilus issue?

@Dino99 thanks for the information, its a step in the right direction now if only there was a url for each file in downloads

---

### Post by veggen on 2010-12-26
Please understand that this is in no way related to Nautilus or Gnome or Ubuntu or Linux, so filing a bug report made 0 sense. How can Nautilus know where you got the file from? It wasn't Nautilus that downloaded it. Only the program that downloaded the file can know where it got it from. And as long as you don't move or rename the file, almost any download manager in the world (including the one in Firefox) will be able to tell where it came from (unless you clear the list, of course).
But, in the long run, you're *much* better off giving your files descriptive names and a meaningful folder structure so you know what's what. Otherwise, you're just asking for losing track.

---

### Post by mikewhatever on 2010-12-26
No, the default Firefox 3.6.13 downloads window shows downloaded file names, dates, and if you right click an entry, you can also get the link. Naming files before the downloading starts will solve the problem of file names making no sense.

---

### Post by afrodeity on 2010-12-26
perhaps its a feature request then? Surely there must be a way of getting a more integrated desktop, one that understands where files come from and what they represent and can thus remind user what they doing there? 

Only way I can think of offhand is to get the browser or downloader to output information to a central db which nautilus then accesses but this sounds a bit complicated to me.

---

### Post by mikewhatever on 2010-12-26
Wouldn't it be more practical to organize your downloads instead of dumping everything into a folder and then trying to figure out what is what and where it came from?

---

### Post by afrodeity on 2010-12-26
Guess that would be better, if Firefox (and other browsers) automatically downloaded into a /Downloads/subfolder with url as the subjectline.

Problem is, you download into the downloads folder, and it all makes sense, (I know there is an option to manually create a folder!!) then next morning you wake up and you can't figure out what the file is doing in Downloads. Going back to the history means having to reconcile what is in the Downloads folder with what is inside browser history, its all very tedious. Add a couple of weeks or months, and you end up with a royal mess.

So I guess this could be solved with a browser plugin.

---

