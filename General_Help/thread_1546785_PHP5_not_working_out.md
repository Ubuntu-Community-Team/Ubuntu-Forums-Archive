---
title: "PHP5 not working out"
date: 2010-08-05
forum: General Help
---

### Post by bbkingwithaj on 2010-08-05
Ok so I have:

a)apt-get install apache2

b)apt-get install php5

c)placed a php test file into my var/www folder

d)go to 127.0.0.1 in my browser and all I see is a blank page, when I should see the php info page.

So what the heck is wrong here?  I figure it's just something I'm too noob to know, yet I can't find anything about it on the net...

---

### Post by WorMzy on 2010-08-05
Did you install libapache2-mod-php5?

```
sudo apt-get install libapache2-mod-php5
```

This tutorial/help page may help you: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by bbkingwithaj on 2010-08-05
*EDIT

Thanks for the tip, found the answer in the link, cheers

---

