---
title: "LAMP Server/UBuntu Problems"
date: 2011-01-26
forum: General Help
---

### Post by Austin Presley on 2011-01-26
Dear All,

 Alright I have just got done installing Ubuntu 10.10 and Lamp, now I know I need to move all my website files to Var/WWW. Well there is a little problem, when I try to delete the two test pages or even edit them. Ubuntu tells me i do not have permission.

And what confuses me the most is i installed the damn OS and i was the first account made one it i am an admin and i still cant delete **** from it....

---

### Post by Rody on 2011-01-26
I think you may want to run gksudo nautilus in a terminal, this will start up nautilus with super user privileges. 

If you are not running an desktop edition then just use sudo to rm the files

---

### Post by Austin Presley on 2011-01-26
Well I'm using desktop edition so what do i do in the terminal?

Edit: i tryed this.... and still can't

austin@SirUtakata:~$ cd /var/www
austin@SirUtakata:/var/www$ rm index.html
rm: remove write-protected regular file `index.html'? y
rm: cannot remove `index.html': Permission denied
austin@SirUtakata:/var/www$

---

### Post by SeijiSensei on 2011-01-26
The Apache server runs with the privileges of the user called "www-data".  As a result, that user owns the /var/www tree.

You have a couple of options:

1)  Add yourself to the www-data group and make sure the files in directories in /var/www are readable and writable by group members.

```

sudo adduser -G www-data austin
sudo chmod g+rw -R /var/www

```

2) Use sudo to become root, then su to the www-data user.

```

sudo su
[enter your password]
su www-data

```

---

### Post by Austin Presley on 2011-01-26
EDIT:

I tryed the gksudo nautilus and it worked

Thanks

---

### Post by wojox on 2011-01-26
```
cd /var/www
```

```
sudo rm index.html
```

```
ls
```

You need SuperUserDO to edit and configure anything outside your home directory. 

You could always create a directory in your /home and link it to that.

---

