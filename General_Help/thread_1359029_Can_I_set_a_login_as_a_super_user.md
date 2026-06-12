---
title: "Can I set a login as a super user"
date: 2009-12-19
forum: General Help
---

### Post by old_dog on 2009-12-19
I am trying to use Bluefish editor to create pages in /var/www not allowed, permissions. I am saving them in my  "temp" then using terminal sudo ......to copy them from temp.
Can I create a super user login so save this mucking about--- life is to short. While I'm on, have a good Christmas everyone

---

### Post by sisco311 on 2009-12-19
> **old_dog said:**
> I am trying to use Bluefish editor to create pages in /var/www not allowed, permissions. I am saving them in my  "temp" then using terminal sudo ......to copy them from temp.
Can I create a super user login so save this mucking about--- life is to short. While I'm on, have a good Christmas everyone

Change the location of the default site from /var/www to a directory in your home (i.e. /home/username/public_html/).

[https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual Hosts]("https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual Hosts")

---

