---
title: "Sharing with samba"
date: 2010-02-21
forum: General Help
---

### Post by snake_eyes on 2010-02-21
Hello,

I have samba on Ubuntu 8.04.4 server, and I have the /var/www, and I have the following homes:
```

/home/user1/www
/home/user2/www
/home/user3/www

```
I ran the following commands to mount the /var/www
```

mount --bind /var/www /home/user1/www
mount --bind /var/www /home/user2/www
mount --bind /var/www /home/user3/www

```
now each user can login to his home without any problem all the samba permission was set correctly, I stumble now with the writing to the same file, such as the user1 was updated the x file in the www the second one wants also to update the x or x2 file, I wanna share the /var/www and to be writable for all users how I can done this?

Cheers,

---

