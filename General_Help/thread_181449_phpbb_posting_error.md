---
title: "phpbb posting error?"
date: 2006-05-24
forum: General Help
---

### Post by lungdart on 2006-05-24
Hey guys, Im using apache2, php5, and mysql 4.x

I tried getting phpbb set up from the installer that phpbb provides and I always got errors saying that my php configuration doesnt support the database type I've picked. (mysql 4.x) After a while of fussing around, I noticed phpbb2 was in apt. I was releived. I installed it, and I added alias in Apache to /usr/share/phpbb2/site/ and chown to my user, as well as chmod 777 recursivly(sp?)

I went on setting up the BB, and when I went to test it I get some php errors! ack!

```

Fatal error: Only variables can be passed by reference in /usr/share/phpbb2/site/posting.php on line 556

```

I checked out line 556 in posting.php and its the line that sends all the post information to the database. All seem to be variables (although theres a tonne of them in that line and I didnt care to see if they were previously set)

Anyone encounter this problem before? Everything else works fine, I can make/edit all forums/groups on there and they update fine so its not a permissions thing. Could there be something up with mysql? Is there any additional setting up with it I don't know about?

Thanks in advanced

---

### Post by lungdart on 2006-05-24
Bump?

---

