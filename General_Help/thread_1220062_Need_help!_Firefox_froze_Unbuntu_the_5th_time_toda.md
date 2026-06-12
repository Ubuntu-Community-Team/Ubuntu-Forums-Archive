---
title: "Need help! Firefox froze Unbuntu the 5th time today..."
date: 2009-07-22
forum: General Help
---

### Post by neogenz on 2009-07-22
Alright, I'm using Ubuntu 9.0.4 installed as a program on XP. 
I just experienced 5th freeze today with firefox. :(
My laptop (Dell Inspiron 700m) would freeze without warning, only mouse cursor moves, but in a loading icon. All clicks and ctrl+alt+backspace or del returned no reaction. Did left the it running for 20min still nothing happened.
I have flashblock addon for firefox so I'm sure flash didn't cause this.
I had to force it to power off then turn in back on, and I'm really worried about this may mess up the file system...
Thoughts anyone? :confused:

---

### Post by neogenz on 2009-07-22
Thanks paddyoquinn, I'm at the "home" folder (places>home folder) but can't find the ".firefox" or ".mozilla" folders :confused:

I got 1.2gb of ram, and was also having some issue with swap management earlier (still testing out new settings).

I found when I'm on smh.com.au, my laptop especially prone to freeze. I don't know why but 3-4 crushs happened when I was on it. And once, ironicly, was when I'm browsing through a thread on firefox froze ubuntu...:(

I've got all three browsers on XP! :D Moved to Opera for a few years, loved it, then moved to firefox as it's fast and got a nice addon call "flashblock", chrome is used mainly for Google doc (faster than firefox for that purpose) as I'm also on a project with a friend. So I be looking forward to your review as I wish to use linux as my main OS. :D

---

### Post by scrooge_74 on 2009-07-22
you need to check to see the hidden files and folder in nautilus or from command line

ls -la

---

### Post by lovinglinux on 2009-07-23
Several posts on these forums recommends moving, renaming or deleting **[COLOR="Sienna"]~/.mozilla[/COLOR]** folder to solve Firefox issues. While this will certainly remove any corrupted Firefox profiles and thus solve many common issues, you should consider that the **[COLOR="Sienna"]~/.mozilla[/COLOR]** folder is also the place where other Mozilla applications might store their profiles (Sunbird, etc), so removing this folder will also remove their settings. 

Firefox profiles are stored under **[COLOR="Sienna"]~/.mozilla/firefox[/COLOR]** or **[COLOR="Sienna"]~/.mozilla/firefox-x.y[/COLOR]** folders, where **[COLOR="Sienna"]x.y[/COLOR]** is the Firefox version. So if you need to remove a Firefox profile to fix a problem, then remove **[COLOR="Sienna"]~/.mozilla/firefox[/COLOR]** or **[COLOR="Sienna"]~/.mozilla/firefox-x.y[/COLOR]** not **[COLOR="Sienna"]~/.mozilla[/COLOR]**. 

Nevertheless, there also no reason to delete the entire profile if you can pinpoint the culprit inside it. Most common Firefox issues can be traced back to a single profile file. So, if you can avoid removing the entire profile, you will be able to preserve other settings like extensions, themes, bookmarks, cookies and passwords.

Check the Firefox tutorial link in my signature.

---

