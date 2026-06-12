---
title: "Downloads box always empty despite lots of downloading"
date: 2011-01-06
forum: General Help
---

### Post by markMDW on 2011-01-06
I've got Ubuntu 10.04 and occasionally download a file from websites using Firefox.  A dialog box always pops up prompting to save the file.  After I <ok> that dialog box another box pops up called "Downloads" that is supposed to contain a list of the files I've downloaded.    It always remains empty despite successfully downloading numerous files over a span of several months.  The "Downloads" box had worked up until a month or two ago.  At time I clicked the one and only button on the box, <Clear List>, and it did just that.  The list of downloads has been clear ever since.  I thought it would clear the list but show new downloads...  and that the list would keep getting longer and longer until I clicked <Clear List> again.  I checked my Downloads folder and the files I've downloaded are there, plus numerous "Copy of ... " files since I would download again and again thinking originally that the file never downloaded.

How do I get the "Downloads" box to show the downloads I've downloaded using Firefox? 
Thanks

---

### Post by markMDW on 2011-01-27
Hi, I still haven't found a solution to this annoyance.  I think I might be confusing folks mentioning that the "Downloads" dialog box stays empty all the time even after downloading new files from Firefox.  

There is a Downloads folder in my home directory.  It stores my downloads from the Internet just fine.  Then there is also something else called "Downloads" that I'm talking about.  This is a dialog box titled "Downloads" that pops up showing the files I've recently downloaded.  It stays empty ALL THE TIME, even after downloading.  It use to list the files I've downloaded, but after clearing the contents using the its one button "[Clear]"... it now stays "clear" ALL THE TIME.  I'm sure the developers intended for it to be cleared and then start accumulating a tally of new files as I download them.

If anyone has an idea its much appreciated ..or even if someone can just confirm they know which box I'm referring to.  Have a great day

---

### Post by wojox on 2011-01-27
Is it notify-osd or something firefox specific? Open a terminal and run this:

```
 notify-send "Click me to close me." -t 0
```

---

### Post by harkumar on 2011-01-27
I dont think the contents of the "Downloads" gets deleted every time for once you selected the option.
There must be some privacy you have assigned to the browser. You should examine it first.

---

### Post by markMDW on 2011-01-28
Thanks for the replies-  It is not notify-send.  I ran the code and get a response saying it is not installed.

I have Firefox and Seamonkey.  With Firefox the "Downloads" dialog window opens showing an empty list of the files I've downloaded, and a notification pops up on the desktop saying the download completed.  I can check the downloads folder and the file will have been properly downloaded.  The Downloads dialog shows nothing.  I also cannot navigate to a folder of my choosing when downloading from Firefox.  It always goes strait the Downloads folder within my Home folder.

But with Seamonkey, I click to download the file and get a dialog box allowing me to navigate to the folder I would like to download into.  After selecting that THEN a "Download Manager" dialog window pops open.   It's just about exactly like the "Downloads" dialog window I get with Firefox but this tool is named "Download Manager" in the window title bar.  They function the same.  In both cases there is a [Clear List] or [Clear] button, and there is a search field to search the contents of the downloads listed within dialog window.  Also there are the three window buttons for Close, Expand or Collapse the window.

However, the "Downloads Manager" works and "Downloads" does not.   I think I'm just going to start using Seamonkey instead of Firefox.  I don't see any benefits to Firefox.

Thanks again!

---

### Post by yanksforever on 2011-05-23
Go to Options at the top of the Firefox menu and then go to options...go to the privacy tab...and check the box that says "Remember download history". That should do it.

---

### Post by markMDW on 2011-12-05
That worked!  All this while I've been seeing the empty downloads dialog box after making downloads.  I just now re-discovered the thread and checking that box solved the problem.  Thanks You!
:KS

---

