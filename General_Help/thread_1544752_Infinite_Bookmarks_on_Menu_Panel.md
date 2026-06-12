---
title: "Infinite Bookmarks on Menu Panel"
date: 2010-08-02
forum: General Help
---

### Post by tcberg2010 on 2010-08-02
I've spent the last couple days running search after search unable to find anything to fix my issues so here I am. I have been using ubuntu for only a couple months now and do not know very much at all regarding it's operation or troubleshooting but i am running into what i believe to be a unique problem.
 
Last week I dropped my keyboard, came back about an hour later, and without realizing the keyboard was on the ground hitting a random button I went to add a bookmark to my menu panel(I think that's what it's called). An unknown amount of the selected bookmark then posted to my menu panel and now i am not even able to select my Applications, Places, or System options without the bookmarked task opening. Is there anyway of clearing out that entire menu panel and having a fresh start? Any help would be appreciated.
 
EDIT: All I did was delete the .gtk-bookmarks file and restart the computer. There were still alot of theme on the panel but i was able to delete them and everything returned to normal.
I would like to thank everyone for their advice. Really appreciate that, especially with a business trip i need my laptop for next week.

---

### Post by corrytonapple on 2010-08-02
Have you let it sit or tryed restarting?

---

### Post by tcberg2010 on 2010-08-02
I've tried both, it's been sitting for a few days now, I've tried multiple reboots, i've also tried to right click delete every one of them to no avail. 

I tried a couple other things I thought were for this but they were for other issues. Thank you.

---

### Post by ankspo71 on 2010-08-02
Hi,
Look inside your home folder for a file called .gtk-bookmarks. That should have a list of all the items in your places menu.
```
/home/yourname/.gtk-bookmarks
```
It is a hidden file, so press Ctrl+H to reveal hidden files when you open your home folder. 
That should be the file you are looking for (to probably edit, or possibly remove), but if not, there is some more info in the following link:
[http://ubuntuforums.org/showthread.php?t=643219](http://ubuntuforums.org/showthread.php?t=643219)
Hope this helps.

---

