---
title: "Creating a text file to start up sudo bash without going to the terminal"
date: 2011-02-26
forum: General Help
---

### Post by jlisec01 on 2011-02-26
Whew, my apologies I tried to sum that up as short as possible.  But yea I just set up apache on my PC and I cant change the permissions by right clicking because "I'm not the owner" and instead of using the chmod command on every file that I would like to edit I would just like to write a script on a text file, save it to my desktop so all I have to do is double click on it and boom I can edit all my files, etc.  However I forgot how to do it, any help?  Most appreciated.

---

### Post by jlisec01 on 2011-02-26
Well I tried in a file I called login.sh, set permissions to executable, i typed the following:

gksudo nautilus

and it worked, but I thought when I originally learned it, I typed more than that.  But is that practical?

---

### Post by towheedm on 2011-02-26
Well you could simply as well open a terminal window and enter

```
gksudo nautilus
```

But remember, running nautilus with root privs may be dangerous.

If you are familiar with the CLI then use:

```
sudo chmod
```

to change permissions.

For instance:
```

sudo chmod 644 /dir/*
```

will change the permissions of all the file in directory <dir> to Owner=root read/write, Group=root and others to read only.

Enter chmod at the CLI for help or check the man pages.

---

