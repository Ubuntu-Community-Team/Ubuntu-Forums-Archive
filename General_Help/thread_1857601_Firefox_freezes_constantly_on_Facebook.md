---
title: "Firefox freezes constantly on Facebook"
date: 2011-10-10
forum: General Help
---

### Post by AceFrehley on 2011-10-10
Hi. I have Ubuntu 11.04 installed, with Firefox 7.01. Almost every time, my machine completely freezes when I am on Facebook, and I have to manually power off the machine. More often than not, it freezes when viewing photos on FB, but it also freezes when I scroll down on the main news feed page.

This happens so often now that I can't even go onto FB. Has anybody else encountered this problem, and if so, do you know a workaround? This also occurred with the last version of Ubuntu, but I thought it was being caused by a faulty drive (guess it could be Firefox too, but..). Since then, I have replaced that drive, and I am still seeing this freezing problem.

Thanks.

---

### Post by hwttdz on 2011-10-11
There are many people using firefox and facebook, so it's likely 
1) a weird configuration in your browser, or 
2) a script many of us don't have run on facebook but you do (it's possible some games cause scripts to run)

So two possibilities would be moving your .mozilla folder to .mozilla_backup and trying again (you'll loose your bookmarks and whatnot, but if you determine this is the issue you can get the data you need from the backup folder).  Failing that grab the noscript addon and seeing if that helps.  Maybe you want to do 2 and then 1?

---

### Post by Furcifer on 2011-10-12
I've had this issue with hanging or extremely slow performance on Facebook ever since Lucid, (click on something or try to scroll, wait 5 to 20 seconds for the action to complete)  

Now, I just did a clean install of 11.04 64-bit with Firefox 7.1 (no add-ons yet), and it's better - no complete freezes - but still very slow and choppy performance on Facebook.  The relatively-new photo-paging popout windows are the WORST.  I'm not sure it's an Ubuntu issue.  I'd guess this more likely has something to do with the linux Firefox implementation. I use Firefox on Vista64 with no significant issues on Facebook.  

This is all running on an Asus G50V laptop with a T5750 2GHz proc and 4GB SDRAM, nVidia GeForce 9700 TM running driver version 173.14.30.

---

### Post by oldfred on 2011-10-12
My wife was complaining and it did this, she said it was better.

Optimize sqlite
[http://web.utk.edu/~jplyon/sqlite/SQLite_optimization_FAQ.html]("http://web.utk.edu/%7Ejplyon/sqlite/SQLite_optimization_FAQ.html")

#!/bin/bash
# [http://pastebin.pl/19714](http://pastebin.pl/19714)

if [ "`ps xo cmd=|grep -c "^firefox$"`" != "0" ]
then printf &#8220;First close firefox..\n&#8221;; exit 1
fi

if ! sqlcmd=&#8221;`which sqlite3 2> /dev/null`&#8221;
then printf &#8220;sqlite3: command not found..\n&#8221;; exit 1
fi

find ~/.mozilla/ -type f -name &#8220;*.sqlite&#8221; -exec $sqlcmd {} VACUUM \;
find ~/.mozilla/ -type f -name &#8220;*.sqlite&#8221; -exec $sqlcmd {} REINDEX \;

-------------------------
do note, vacuum AFTER clearing all the cache, otherwise YES you won&#8217;t see a difference.
also if you learn SQL, you can remove items by dates, but the date are in system offset. eg cookies, are all or thing but the database has a date when it was stored. so if you want to keep recently and remove others, then try the SQL query method

---

### Post by darthenstein on 2011-10-15
I had this exact problem, I remedied it by updating my video card drivers.

Click the system button in the top right corner, go System Settings... > Additional Drivers... and there should be some new drivers in there.  If you are unsure of what is going on there, post what drivers you have listed and we can help you more!

Facebook is just very video/flash demanding, but it sure is awesome when it works!

---

