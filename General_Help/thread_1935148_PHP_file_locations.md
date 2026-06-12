---
title: "PHP file locations"
date: 2012-03-03
forum: General Help
---

### Post by maxhud on 2012-03-03
So when I execute a PHP function, such as exec(), unlink(), or file_exists(), I have to put "/var/www" in front of the actual file location.

When I have used hosting services in the past, files have been located in a public_html/ folder, but I set up my own web server and files are located in var/www/.

So for example when a file used to be public_html/file.php, I would refer to it as anyphpfunction("/file.php") or if a file was public_html/folder/file.php I would refer to it as anyphpfunction("/folder/file.php"), but now it doesn't work unless I use anyphpfunction("/var/www/file.php") or anyphpfunction("/var/www/folder/file.php")

How do I change it so that it works the way I am used to?

Thanks

---

### Post by GWBouge on 2012-03-03
Do you have to do this with simple html links as well (such as img or href)?

---

### Post by maxhud on 2012-03-06
No it's only specific php functions like exec() or unlink()

functions like include 'file.php'; work fine

thanks

---

### Post by maxhud on 2012-03-09
bump

---

### Post by dragonfly41 on 2012-03-09
I think if you search "public_html" in this forum you might find some answers.

You need to specify DocumentRoot.

e.g. I've moved mine from /var/www/ .. to .. /home/username/public_html/

---

