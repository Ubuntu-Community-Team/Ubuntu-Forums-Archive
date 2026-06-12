---
title: "User &quot;real&quot; names don't match"
date: 2012-09-19
forum: General Help
---

### Post by Stonecold1995 on 2012-09-19
My "real" name displayed under Settings > Account Details seems to be different from what is set at Settings > User Management.  Under User Management, I have my full name, but under Account Details it says my name is "Student".  Long story, but this is how I'm guessing it happened...  My old computer was a school computer with Windows, and the admin account was admin and my account was Student.  After I left that school, the admin account was deleted and admin privileges were given to Student.  Later, I installed Kubuntu through Wubi, which kept Student as my name.  After Windows started getting slow and unstable, I decided to "rescue" my Kubuntu install by migrating from Wubi to a real partition, and deleting Windows.  This also kept my name as Student.  *Then* I bought a whole new computer, installed Kubuntu on it, and transferred /home from my old one to the new one, and that's the one I'm typing on right now.

As far as I know, it only says I'm "Student" on Settings > Account Details, but nowhere else.  How can I change this so it reflects my account's actual "real" name?

[[IMG]http://www.pictureshack.us/thumbs/85722_name-final.png[/IMG]](http://www.pictureshack.us/images/85722_name-final.png)

---

### Post by Stonecold1995 on 2012-09-28
Anyone?

---

### Post by Stonecold1995 on 2012-10-10
bump

---

### Post by critin on 2012-10-11
So student is not your root name?  

You might check here.  Check for your version on the site, though instructions should be the same, it's better to find the right version.   Be sure to change the correct name.  lol

[http://www.liberiangeek.net/2012/03/how-to-change-your-username-in-ubuntu-11-10-oneiric-ocelot/](http://www.liberiangeek.net/2012/03/how-to-change-your-username-in-ubuntu-11-10-oneiric-ocelot/)

---

### Post by Stonecold1995 on 2012-10-11
Didn't work. It's not my "user name" that's shown incorrectly, it's my "real name".  It displays correctly on other applications, but just not under "User Information" in settings.

If I know the location of the config file for those settings, I could probably change it through that.

---

### Post by Wim Sturkenboom on 2012-10-11
Start a terminal and run

```

grep -r Student * 2>/dev/null

```
will search for the word _Student_ in all files. Run this first from your home directory, that should be sufficient. If not, run it from the root directory.

Both exercises can take long.

You can pipe the result through 'less' or redirect them to a file for later analysis.


PS
Although I don't think it's the case, you can have a quick look at /etc/passwd to see if it's set there. Before you go through the above time consuming exercise.

```

grep Student /etc/passwd

```

---

### Post by Stonecold1995 on 2012-10-16
```
grep -r Student * 2>/dev/null
```

That gave me no relevant results.

```
grep Student /etc/passwd
```

It wasn't there.

---

### Post by Stonecold1995 on 2012-10-30
bump

---

