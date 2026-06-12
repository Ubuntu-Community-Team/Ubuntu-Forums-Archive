---
title: "Ubuntu Splash Screen Messed Up"
date: 2011-01-26
forum: General Help
---

### Post by borth92 on 2011-01-26
Since updating my graphics driver on ubuntu 10.10, My splash screen has been inconsistant and messed up. Sometimes ill get random command lines mixed in with the usual splash, sometimes the splash wont show and it will just be black till the desktop appears, sometimes it flashes on and off. I originally tried fixing the resolution and just made the problem worse. Then I tried installing a new splash via gnome-look.org, but it just made my shut-down splash blank and didnt effect my splash at startup. I just want the original splash that ubuntu is supposed to have. please help, should I maybe reinstall python? idk where to go from here

---

### Post by drewsus on 2011-01-26
what graphics card do you have? 

Might this be your issue/solution?
[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)
[SIZE="1"](applies to 10.10 as well)[/SIZE]

---

### Post by MrRichard on 2011-01-26
> **drewsus said:**
> what graphics card do you have? 

Might this be your issue/solution?
[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)
[SIZE="1"](applies to 10.10 as well)[/SIZE]

If you have an ATI graphics card, the above should work.

I've heard that this is caused by the drivers loading too late in the boot process...or something along the lines of it. Hopefully this little issue will be fixed in Natty :)

---

### Post by drewsus on 2011-01-26
If that is the real issue then I think I may be able to help with that too. But, lets see what happens following the first suggestion.

---

### Post by borth92 on 2011-01-28
Sorry for the late reply, had business meetings all day yesterday. I have a nVidia Geforce 8400 or so. not sure if that fall under the category of the fix you named. Will try fix in the morning

---

### Post by borth92 on 2011-01-28
GOT IT!

I had tried your fix and it didn't work. Right before giving up I realized I use BURG so i needed to change the resolution on the burg.conf file the same way as the grub.conf. After that my splash looks great. Hopefully others who have the same brainfart learn from my mistake.

---

### Post by drewsus on 2011-01-29
Perfect! I too use burg and it took me a bit of brain stretching to realize that I had to make changes to the burg.conf as well. Glad you got it sorted. 
You might want to check out this great plymouth theme:
[http://www.webupd8.org/2011/01/earth-sunrise-is-gorgeous-plymouth.html](http://www.webupd8.org/2011/01/earth-sunrise-is-gorgeous-plymouth.html)

---

