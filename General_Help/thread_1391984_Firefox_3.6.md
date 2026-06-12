---
title: "Firefox 3.6"
date: 2010-01-27
forum: General Help
---

### Post by gdonwallace on 2010-01-27
OK, so I decided to download and use Firefox 3.6.  I also installed htop as I have read that it is easier to use than the regular top command.  

The first time I run htop, is see /opt/firefox/firefox-bin running over 10 times.  Sometimes it will be a little less, but it always seems to increase to back over 10 processes.  I can exit out of Firefox, and they all disappear.  But when I start it back up, there are 15 processes running of the same name.  

I only have 2 add-ons currently installed so it can't be that.

Anyone else having the same issue.

I have not checked Firefox support for any clues, but that is my next stop.  

If I find anything, I will post it here.

---

### Post by oldos2er on 2010-01-27
Sounds normal to me. A given program might start X number of processes to facilitate the tasks it needs to do, which helps the program do its work faster.

---

### Post by sebastianabate on 2010-01-27
That's because htop shows all the threads of a given proccess.

You can start htop, press F2 (Setup), and in the Display Options check Hide Userland Threads. The same goes to Hide kernel Threads.

---

