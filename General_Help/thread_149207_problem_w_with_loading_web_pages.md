---
title: "problem w with loading web pages"
date: 2006-03-23
forum: General Help
---

### Post by tomex on 2006-03-23
as in the title i have problem with loadig internet pages via firefox (also via konquer).  It'd pretty strange becouase one pages are loaded but the other not. Example: [http://fizjoterapia.xt.pl](http://fizjoterapia.xt.pl) doesen't  work but [http://www.toya.net.pl/~ciejka](http://www.toya.net.pl/~ciejka) is ok. (it the same page). I could give u dozens of exempes. (it's quite annoing!)  Letters 'www' doesnt. mind I chacked it. whats wrong? Please HELP me..
(sorry for my english...:/)

---

### Post by dragonfyre13 on 2006-03-23
Look through settings (edit->preferences) and check for anything talking about redirection. That could very well be the problem. Also, go through the whole preferences section, and make sure to set it correctly.

Check to make sure IPv6 is off. (do a search on the forums if you don't know how, or it is on the wiki.)

refresh the page on one of the pages that will load. It could be loading it from cache, and thus only look like you are connected.

---

### Post by tomex on 2006-03-23
I did as u adviced me:
1. chacked all preferences in firefox.
2. i am sure that i have internet connection (google works, comunicator etc..)
3. the value in firefox config "network.dns disableIPV6" i chacked true and false (doesnt work)
4. i created file 'bad_list' with value: "alias net-pf-10 off" in /etc/modprobe.d as it was written in one of the threads.

during booting i noticed that 'synchronizing to ubuntu.clock or something' is failed. it was ok when i could surf via internet without any porblems 

any clues? please help becouse i don't want to reinstall the system for the 4th time :/

---

### Post by tomex on 2006-03-24
has smb the same problem?? please give me some odvice..
thx

---

