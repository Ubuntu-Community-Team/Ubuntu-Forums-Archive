---
title: "Firefox Java problem with playing yahoo pool etc.."
date: 2010-09-23
forum: General Help
---

### Post by ontherooftop on 2010-09-23
I got this working before, but now I have a freshly installed Ubuntu 10.04 and I wanna play yahoo pool and I followed all those crazy insane commands they posted but they (java) didn't help at all, their support and help is really poor as I get errors like directory does not exist or no such file.
I basically installed the jre-6u21-linux-i586.bin file in my home directory like and used all their commands like cd /home and all that. Here is my ls output they say always to check, but it seems like I installed it but I can't get it installed with firefox together.

laptop:~$ ls
Desktop    dwhelper               FrostWire                Music     Templates
Documents  examples.desktop       jre1.6.0_21              Pictures  Videos
Downloads  Firefox_wallpaper.png  jre-6u21-linux-i586.bin  Public

---

### Post by lykeion on 2010-09-23
Administration > Synaptic Package Manager
Enter "icedtea6-plugin" in Quick search field 
Right-click icedtea6-plugin > Mark for removal
<see 01.png>

Settings > Repositories > Select Other Software tab
Make sure the line with "http://archive.canonical.com/ubuntu lucid partner" is ticked
<see 02.png>

Click Reload button
Enter "sun-java6-plugin" in Quick search field 
Right-click sun-java6-plugin > Mark for installation
<see 03.png>

Restart Firefox and try Yahoo Pool again

---

### Post by ontherooftop on 2010-09-23
Thanks I will try it, thanks for responding. How do I give you points on this site?
Yes it works, really easy just a few clicks and what it works. The Java site has 
like 10 ridiculous commands that are a pain in the you know what and sometimes work 
and sometimes get errors, when they should just mention the 3 clicks to do lol. I
wanna give you points but don't know how. Thanks

---

### Post by lykeion on 2010-09-23
:"> I don't need no points, just glad to be of help.
But you could tag this thread as SOLVED (to let others find help easily), explained here:
[http://ubuntuforums.org/showpost.php?p=4527051&postcount=6](http://ubuntuforums.org/showpost.php?p=4527051&postcount=6)

---

### Post by kinkinkijkin on 2010-09-25
You lead me to this thread but this method isn't working for me. I search sun-java6-plugin after checking the repository required, and nothing showed up.

EDIT: did a name-only advanced search, it came up.

---

