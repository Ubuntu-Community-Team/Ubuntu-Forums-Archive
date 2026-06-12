---
title: "apache permission on /var/www"
date: 2011-12-02
forum: General Help
---

### Post by qwertyjjj on 2011-12-02
I just istalled apache2 and was going to use this as my development machine.
However, I can't copy anything into /var/www
I assume this is because it is owned by root or apache.
How can I add permissions for my normal ubuntu user login to that folder?

---

### Post by MG&amp;TL on 2011-12-02
Either:

```
gksu nautilus
```

will launch a root file browser.

or 

```
sudo cp files /var/www/
```

will also work.

Read up on root access in ubuntu.

---

### Post by lisati on 2011-12-02
> **MG&TL said:**
> 
Read up on root access in ubuntu.
Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by qwertyjjj on 2011-12-02
> **lisati said:**
> Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

sudo is all done in the terminal though isn;t it?
I just want to use the GUI to move and edit files.
Easier to change /var/www to 777?

---

### Post by Lars Noodén on 2011-12-02
If you're the only one using the directory then you can simply take ownership of it:

```

sudo chown qwertyjjj  /var/www

```

If you're sharing access with others then you need to set group permissions for a group you and the others are all members of.  In this example it is a group called 'webmasters'

```

sudo chgrp -R webmasters /var/www
sudo find /var/www/ -type d -exec chmod g=rwxs {} \;

```

---

### Post by snowpine on 2011-12-02
I can assure you that professional web developers aren't logged in as root all day long. :)

There are two possible ways to set this up correctly:

1. Create a web development group, add your user to the group, chown /var/www to the group.

or

2. Symlink /var/www to your /home folder so you can edit the files as your normal user.

Both of these methods are described here: [http://askubuntu.com/questions/19898/whats-the-simplest-way-to-add-files-to-var-www](http://askubuntu.com/questions/19898/whats-the-simplest-way-to-add-files-to-var-www)

IMHO, running Natilus as root should be a last resort; easier in the long run to set it up correctly. :)

---

