---
title: "ktorrent"
date: 2009-08-28
forum: General Help
---

### Post by whalescreams on 2009-08-28
I use demonoid.com and waffles.fm for torrents.... when I choose to download them firefox gives me the option to save or open with... either way i go about it I cant seem to find a way to link it to ktorrent to download...  Im sure it something simple but this is all new to me

---

### Post by baseface on 2009-08-28
save it and open it in ktorrent.

---

### Post by Sxeptomaniac on 2009-08-28
Yes, there is a way. I had the same problem for a long time.  

Use ```
whereis ktorrent
``` in a terminal to get the full path to the program (probably /usr/bin/ktorrent).  Next time Firefox asks you what to do with a torrent file, check the "Do this automatically for files like this from now on" box, choose "Open with" and open the "Browse..." dialogue.  Paste the location of ktorrent in that, and it should work automatically from now on.

---

### Post by whalescreams on 2009-08-28
SO i did that... and it said The application you chose ("(null)") could not be found.  Check the file name or choose another application

---

### Post by whalescreams on 2009-08-28
and trying to save and open it.. i couldnt find ktorrent......... so i copy and pasted like the last one said... it added ktorrent as an option but from there it does nothing..

---

### Post by oldos2er on 2009-08-28
In Firefox, open Edit, Preferences, Applications, BitTorrent seed file, click the Action tab, in the drop down menu, choose ktorrent.

---

### Post by whalescreams on 2009-08-28
after applications there is nothing that says BitTorrent Seed File.... and everything that is there under the dropdown menus ktorrent isnt an option and ive tried adding it to the launch applications two ways (finding the location through the terminal and just typing it in) but neither does anything still

---

### Post by Sxeptomaniac on 2009-08-28
OK, test out closing ktorrent and then starting it in the terminal with the path you got from whereis.  If that works, then try not typing the path into the "Browse..." dialogue in Firefox.  Instead, use the mouse to go to root, then (if your path is the same as mine) click on the usr, then bin folders, then choose ktorrent and click "Open".

If starting it from terminal doesn't work, we need to figure out why that might be, so maybe post what you're using for the path here.

Edit: I just tested out the procedure again, and it works on my computer.

---

### Post by whalescreams on 2009-08-28
bash: ktorrent:: command not found is what displays in terminal when i put the path it gave me... it does open when i just type in ktorrent

and it opens if i go the root path from my desktop... but if i use the helper application when i choose to download now it says this

Error stating file '/home/whalescreams/Documents/ktorrent: /usr/bin/ktorrent /usr/share/man/man1': No such file or directory

and i choose root on that app and it never opens.. just keeps sitting there processing something

---

### Post by Sxeptomaniac on 2009-08-29
Sorry, this is my mistake; I should have been clearer regarding the use of whereis.

Whereis shows you where everything from a certain package installs, which may include multiple directories separated by spaces.  You're pasting two directories together instead of just the one you need.  The first part of the whereis output, "/usr/bin/ktorrent", is the location of the program, and the second part, "/usr/share/man/man1" is the location of the manual pages that were also installed with the ktorrent package.  So, if you just use "/usr/bin/ktorrent", it should work.

---

### Post by whalescreams on 2009-08-29
ok.. that worked... thank you....

the only thing now is the download speed is ridiculously slow... everything downloaded much faster with utorrent and windows for me.... is there some kind of settings or something that i could change that might increase this

---

### Post by Sxeptomaniac on 2009-08-29
Check your configuration menu and see if a maximum download speed is set (it's under the Network tab).

---

### Post by whalescreams on 2009-08-30
yeah tried that..... fastest ive seen one download was only 150 kiB/s (some even had hundreds of seeders..... thanks for your help again.... running into so many issues with kubuntu just to get things started

---

