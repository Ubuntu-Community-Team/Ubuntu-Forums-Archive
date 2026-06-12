---
title: "apache 2 server"
date: 2012-05-07
forum: General Help
---

### Post by Nessto on 2012-05-07
Running ubuntu 10.10 server edition just ssh. have the gnome gui interface. cant figure out how to give my self write permission to the www folder to change my webpage. also not quite sure how to make my [www.BLA.whatever](www.BLA.whatever). Looking for a link to a great source of information or atleast how to change permissions.

---

### Post by 2F4U on 2012-05-07
Did you try to add yourself to the group that owns the folder?

---

### Post by Lars Noodén on 2012-05-07
If you are the only user of the machine, then one way is to take ownership of the directory and its contents:

```

sudo chown -R nessto:nessto /var/www

```

If you are sharing access with other users, then you'll have to use groups:
[http://ubuntuforums.org/showpost.php?p=11714082&postcount=2](http://ubuntuforums.org/showpost.php?p=11714082&postcount=2)

(This gets asked often enough that it should be added to a FAQ or the default settings might be changed.)

---

### Post by Nessto on 2012-05-08
Perfect, That was the command i was looking for . thanks all for the help

---

