---
title: "Chmod subfolders"
date: 2006-06-02
forum: General Help
---

### Post by stiankarlsen on 2006-06-02
I have a rather large dir laying around, which I'm currently sharing on my webserver, the problem is that all files/folders are set to chmod 600, so you can't access them through the server.

By running chmod 744 /my/folder*.*
I am able to chmod all files in the folder the way I want to, but there's also like 30 or 40 subfolders, is there any command that can chmod them and their content as well, or do I have to go through them all, 1 by 1 to get the job done.

Thanks.

---

### Post by jongkind on 2006-06-02
You can do this by adding -R to the command line

---

### Post by stiankarlsen on 2006-06-02
By doing sudo chmod 644 MOVIES/*.* -R
I ended up giving all content of every subfolder permisions 0

what went wrong here?

edit.

I'm sorry, got it working. Thanks a lot!

---

### Post by i386DX on 2006-06-02
Is there also a way to do this in Gnome? As far as I know in Gnome you can only change the ownership of one file or folder. So you have to use the CLI for this...

---

### Post by lkagan on 2006-06-02
I'm glad you got it working.  Permissions can be tricky.  But just for your information, it's generally considered bad netiquite to ask a question on a forum or list before checking the man page for a command.  man chmod would have answered this question for you.  I know man pages are often times quite cryptic but you should always check there first.  There's also two more options for seeking help on your own system, check the commands 'info' and 'help'.

By the way, I'm the admin for a group of web developers so here's some permission info that comes in handy.

Add everyone working on the web site to the www-data group by opening up the /etc/group file and append the names in a comma separated list.  Then  ensure the group owner of the web directory structure is recursively owned by www-data.  Now recursively give the group full access.
```

chgrp -R www-data /path/to/web/root
chmod -R g+rwx /path/to/web/root

```

Larry

---

### Post by stiankarlsen on 2006-06-05
Thanks a lot, i should have looked around a bit more first.

My bad, but again, thanks

---

### Post by exclipy on 2006-06-06
Is it possible to set permissions recursively, but only on directories - not files?  I often find myself needing to set +x permissions on a directory tree, but I don't want to make all the files executable as well.

---

### Post by lkagan on 2006-06-06
Very good question.

```
 chmod +x `find . -type d`
```

The dot (.) represents the current directory.  You can simply replace it with the absolute or relative path of the top of the directory tree in which you want to traverse.

Larry

---

### Post by exclipy on 2006-06-07
Sweet - thanks!

---

### Post by barbieric on 2006-08-30
Hi.

I have the same problem. Searching in Google, I've found a very interesting link:

[http://blogs.gnome.org/view/cneumair/2006/03/06/0](http://blogs.gnome.org/view/cneumair/2006/03/06/0)

I hope this can help you.

---

### Post by mssever on 2006-08-31
> **barbieric said:**
> Hi.

I have the same problem. Searching in Google, I've found a very interesting link:

[http://blogs.gnome.org/view/cneumair/2006/03/06/0](http://blogs.gnome.org/view/cneumair/2006/03/06/0)

I hope this can help you.
I can't wait for the recursion and chmod parts to be included in a "normal" version. But I'm not terribly excited about replacing checkboxes with drop-downs.

> **i386DX said:**
> Is there also a way to do this in Gnome? As far as I know in Gnome you can only change the ownership of one file or folder. So you have to use the CLI for this...
I understand that both Konqueror and Thunar can do this recursively.

---

