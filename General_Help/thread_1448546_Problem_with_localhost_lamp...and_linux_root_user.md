---
title: "Problem with localhost lamp...and linux root user"
date: 2010-04-06
forum: General Help
---

### Post by Amae on 2010-04-06
Hi,

I wasn't sure on how to name this post, because the problem isn't with localhost itself, I just have the following issue:

I installed lamp, and my localhost works "perfectly", atleast I can see what I have con my www folder from my browser. The problem is that, I can't make any changes, or have problem displaying things and editing things "normaly" because of the ubuntu root user. I have to be editing things from the terminal, using sudo su, starting nautilus from the terminal so I can type the root pasword and such. 

I installed wordpress, and many things are crazy just because of this problem. It happened on my home pc, on my laptop, and on my work pc.

I would like to find a way to solve this, I really wouldn't like to install windows so that I can actually use my localhost normally... -.-

---

### Post by Iowan on 2010-04-06
[Here]("https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts") is a help page that discusses virtual hosts and moving DocumentRoot (to somewhere easier for you to access). Notice this note:> Please do not make any edits to this article. Its contents are currently under review and being merged with the Ubuntu Server Guide. To find the Ubuntu Server Guide related to your specific version, please go to:

    *

      [https://help.ubuntu.com/](https://help.ubuntu.com/) and click on Ubuntu Server Guide

---

### Post by Amae on 2010-04-08
Thank you, I will read that. :)

---

### Post by indytim on 2010-04-08
The other approach is to change the owner and group to your user id in /var/www

```

$sudo chgrp -R your-user-id /var/www
$sudo chown -R your-user-id /var/www 

```

The "-R" is a recursive flag meaning that the changes apply to all child folders and files contained within /var/www.

Indytim

---

