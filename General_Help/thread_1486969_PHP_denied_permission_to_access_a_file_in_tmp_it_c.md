---
title: "PHP denied permission to access a file in /tmp it created"
date: 2010-05-18
forum: General Help
---

### Post by Vunutus on 2010-05-18
I have a PHP script that called the tempnam function to make a file in /tmp for later use.

The file is created properly. Its owner and group are set to www-data and it has RW permissions for owner only. When my script tries to read it, I get a permission denied exception.

What gives? www-data is apache's user and PHP is running under apache so shouldn't it be able to access this file?

---

### Post by Vunutus on 2010-05-19
bump

---

### Post by AlexDudko on 2010-05-19
Do you set permissions for the created file in your script?

---

### Post by Vunutus on 2010-05-19
> **AlexDudko said:**
> Do you set permissions for the created file in your script?

No, I don't know of any way to do that, and neither tmpfile() or tempnam() have any parameters related to file permissions. Besides, if I can't even open a file I doubt I could change permissions on it.

I posted this here because I'm thinking it's a general Linux and/or Apache configuration problem. None of the guides I've found for creating temporary files mention permissions or anything that could cause a problem here.

---

### Post by AlexDudko on 2010-05-19
Have you read PHP manual [http://ua2.php.net/manual/en/function.fopen.php](http://ua2.php.net/manual/en/function.fopen.php) ?

---

