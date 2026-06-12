---
title: "No HOWTO for permissions?"
date: 2006-06-03
forum: General Help
---

### Post by nami on 2006-06-03
This is going to make me sound like a real noobi!

I have an icon on my desktop which i can't smily delete:

[[IMG]http://img323.imageshack.us/img323/9180/screenshot7da.th.jpg[/IMG]](http://img323.imageshack.us/img323/9180/screenshot7da.jpg)

How do I change the permissions so I can delete it?

---

### Post by xXx 0wn3d xXx on 2006-06-03
[QUOTE=nami]This is going to make me sound like a real noobi!

I have an icon on my desktop which i can't smily delete:

[[IMG]http://img323.imageshack.us/img323/9180/screenshot7da.th.jpg[/IMG]](http://img323.imageshack.us/img323/9180/screenshot7da.jpg)

How do I change the permissions so I can delete it?[/QUOTE]
Try:

> sudo chmod 777 /path/or/nameof/file
Then delete it or try this:

> sudo rm -f nameoffile

---

### Post by B0rsuk on 2006-06-03
You asked for HOWTO, here it is:

[http://en.wikipedia.org/wiki/Permissions](http://en.wikipedia.org/wiki/Permissions)
[http://en.wikipedia.org/wiki/Chmod](http://en.wikipedia.org/wiki/Chmod)

---

### Post by KrazyPenguin on 2006-06-03
[QUOTE=nami]This is going to make me sound like a real noobi!

I have an icon on my desktop which i can't smily delete:

[[IMG]http://img323.imageshack.us/img323/9180/screenshot7da.th.jpg[/IMG]](http://img323.imageshack.us/img323/9180/screenshot7da.jpg)

How do I change the permissions so I can delete it?[/QUOTE]


Open a terminal:
 cd Desktop
 ls -l

Now the names of the files will be displayed.
Then do what the dude said in the previous post.

Hope that helps.

---

### Post by nami on 2006-06-03
Thank you all!

---

### Post by nami on 2006-06-10
Just noticed a slight problem this this.  The instructions above all me to delete those icons from the desktop, but I can't remove them from the Wastebasket!

Any ideas?

---

### Post by MakubeX on 2006-06-10
Wastebasket? Is that the Trash location? Then go "locate" the Trash folder and delete it there.

---

### Post by nami on 2006-06-10
Where is that folder?

---

### Post by patrickfromspain on 2006-06-10
you could  do: sudo rm -rf  cd /to/the/trash folder_name

---

### Post by blackjack6.21.91 on 2006-06-10
The trash folder is located in your home folder.  By default called .Trash (at least on my computer).  It is hidden by default.  Press <Control><H> to see it.  But I think all of the preceding instructions wiped the file from your computer, not deleted it.

---

### Post by nami on 2006-06-10
Thanks for the info.  Its gone "finally" from the trash!

---

### Post by nami on 2007-12-04
how do i change permission of a folder, so any files inside it also change, and any new files in there should automatically change to the same permissions of the folder.

how do i do that?

i am trying to change /var/www so i can read/write/delete/modify/create files into that folder with any program...

---

