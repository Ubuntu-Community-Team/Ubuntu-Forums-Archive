---
title: "java (and flash?) not working"
date: 2009-07-28
forum: General Help
---

### Post by privatejarhead on 2009-07-28
well, i finally got around to installing ubuntu (9.04 32-bit) on my system (Toshiba Satellite L505). i wanted to see if everything would work with what i usually do on the computer. I've tried out playing mp3 files and sure enough, ubuntu recognized that it needed the codexes, so it installed them without problem. then i tried playing a windows movie maker film and that didnt work, no codex was offered, although i didnt care for that, so no worries (maybe ill figure it out later). then i tried running java on my computer. the only java-based program i know of (runescape...yea, horrible game...) wouldn't run. at first, i wasnt concerned about it, thinking a simple install would work. i went to the java website and downloaded the linux version of the current java program (java 6 i beleive), but when i tried it, it wouldnt run. then i remembered ubuntu-restricted-extras, so i ran terminal and installed that. still no java -.-... i have another code i might try (sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-jdk), but i want to get people's thoughts about why java isnt working on my laptop.

as a side though, i tried running flash (using a game on freeworldgroup.com) after installing restricted extras, and i think it works, although after 4 minutes of loading, it was at 3%. i have an average download/upload speed of 650kbps/140kbps, so i know my internet connection wouldnt be that slow. any help on either issue? thanks in advance.


edit-
youtube runs off of flash and it works perfectly....maybe its just the website.
also forgot to add that i tried installing java as a plugin through firefox...didnt work.

---

### Post by CrusaderAD on 2009-07-28
Use adobe flash:

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Works for me.

---

### Post by speedwell68 on 2009-07-28
Try your command for Java and this for flash...

sudo apt-get install flash-plugin-nonfree

---

### Post by privatejarhead on 2009-07-28
> **raptormanad said:**
> Use adobe flash:

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Works for me.



thank, the flash programs work now, albeit they still load a little slow (this is because of my slow internet connection, no relation to ubuntu), so im happy about that. as for java, i did the code i posted, but i still cant run java in firefox 3.5. ill look for other ways to getting it to work, but thankfully this wont kill ubuntu for me, so not a huge issue. java's just being a minor annoyance that ill try to fix sometime.

---

