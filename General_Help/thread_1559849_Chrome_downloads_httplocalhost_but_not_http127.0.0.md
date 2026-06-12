---
title: "Chrome downloads http://localhost/ but not http://127.0.0.1/"
date: 2010-08-24
forum: General Help
---

### Post by teabee89 on 2010-08-24
Hello,

Here are the app versions:
- Ubuntu 10.04 Lucid Lynx
- Chrome 5.0.375.127 (with or without --enable-ipv6)
- Apache 2.2.14

When I go to [http://localhost/](http://localhost/) a file named "download" gets downloaded. I have no such file in my server, thus this is part of Chrome's strangenesses.
The file contains "<?php phpinfo(); ?>" the same content as my phpinfo.php file.

But I do have an index.html file containing just "It Works", but it doesn't get viewed unless I type explicitly [http://localhost/index.html](http://localhost/index.html)

BUT, when I type [http://127.0.0.1/](http://127.0.0.1/) without adding index.html to the URL, it works!

The strange thing is that this issue does not exist with Firefox. So when I type [http://localhost/](http://localhost/) I get my index.html as I expect it.


Before trying with Firefox, I thought it was an issue with my apache config, but now I don't know if Apache, Chrome, or both are the source of the problem.

Thanks for any help!

---

### Post by teabee89 on 2010-08-24
Anyone? Anything?

---

### Post by uberdave on 2010-10-15
just had the same issue with 10.10, thought I was going crazy at first...

---

### Post by gpix13 on 2011-06-21
BUMP

Sorry if you guys have figured this out or not, but I just had the same issue after uninstall some web server packages and all I had to do was go into Google Chrome's Preferences and clear all of the browsing data. 'http://localhost/' then quit downloading that 'download' file and I was able to view my index and everything just fine.

Jake

---

### Post by AlphaLexman on 2011-06-21
Do you have a '**/var/www/**' directory?
Does it contain a file '**index.html**'?

---

### Post by slooksterpsv on 2011-06-21
> **teabee89 said:**
> Hello,

Here are the app versions:
- Ubuntu 10.04 Lucid Lynx
- Chrome 5.0.375.127 (with or without --enable-ipv6)
- Apache 2.2.14

When I go to [http://localhost/](http://localhost/) a file named "download" gets downloaded. I have no such file in my server, thus this is part of Chrome's strangenesses.
The file contains "<?php phpinfo(); ?>" the same content as my phpinfo.php file.

But I do have an index.html file containing just "It Works", but it doesn't get viewed unless I type explicitly [http://localhost/index.html](http://localhost/index.html)

BUT, when I type [http://127.0.0.1/](http://127.0.0.1/) without adding index.html to the URL, it works!

The strange thing is that this issue does not exist with Firefox. So when I type [http://localhost/](http://localhost/) I get my index.html as I expect it.


Before trying with Firefox, I thought it was an issue with my apache config, but now I don't know if Apache, Chrome, or both are the source of the problem.

Thanks for any help!

Hahaha, yeah I run into this often. Ok so you installed the PHP addon for Apache, did you run 
sudo a2enmod php5
Um.... if that doesn't work try modifying the virtual host and creating a new one specifically for local host. When I find the information on how I fixed mine, I'll repost back, but I have had this issue often and usually it's something stupid like I didn't install x, y, z, or enable x, y or z

---

### Post by sportsdude81 on 2012-03-02
I just ran into this problem today.  I know this is an old thread, but if anybody could find another solution for this or give me some steps to trouble shoot that would be amazing.  Thanks in advance

Edit:

Never mind forgot to clear my browser cache.  Thanks anyways.

---

