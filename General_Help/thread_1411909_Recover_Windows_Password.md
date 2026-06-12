---
title: "Recover Windows Password"
date: 2010-02-20
forum: General Help
---

### Post by alexboi111 on 2010-02-20
I have Ubuntu Netbook remix installed on my netbook, it's installed alongside Windows XP. Is there a way to recover Windows passwords through Ubuntu?

---

### Post by underquark on 2010-02-20
ubuntu will not have changed your Windows passwords so - fear not - you can still get into Windows and it will be just as just as secure as before.

---

### Post by alexboi111 on 2010-02-20
> **underquark said:**
> ubuntu will not have changed your Windows passwords so - fear not - you can still get into Windows and it will be just as just as secure as before.

I know that, but there are some logons I need the password to.

---

### Post by nerdy_kid on 2010-02-20
as long as you use only alphanumeric passwords on the win install, then life is simple:
```

sudo apt-get install ophcrack

```
download some tables:
[http://ophcrack.sourceforge.net/tables.php](http://ophcrack.sourceforge.net/tables.php)
then 
```

ophcrack

```

make sure your windows partition is mounted.

click tables...select the table you downloaded (you can use more then one at a time) hit install...select the dir of the extracted table.  Back at the main screen, hit load encrypted SAM.  select WINDOWS/system32/config on the windows partition.  then hit crack :)  if all is well...the passwords should show up.  If not, then try downloading a different table.  Good luck ;)

---

### Post by alexboi111 on 2010-02-21
Okay, thanks a lot for the help!

---

### Post by annyyu22 on 2010-03-01
I hope this can help you.last month my sister meet the same problem,and then we solved it as follow.There is a way to reset the password and it doesn't involve reformatting and reunstalling Windows. The solution is called Windows Password Key 8.0. It is the most popular and safe solution for resetting your Windows password until now. You can down it from: [http://www.lostwindowspassword.com](http://www.lostwindowspassword.com)

---

