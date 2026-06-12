---
title: "Help with find | grep | rm -r"
date: 2012-09-04
forum: General Help
---

### Post by MusicalRobots on 2012-09-04
Hi guys,

I've got a large project which I need to wipe out a certain subset of folders and all of their contents.

I'm trying to use:

sudo find | grep test- | rm -r

I get the files I'm looking for but I get a permission denied error when the rm attempts to occur.  As I understand this it's because the rm is not actually being executed as root. 

I've seen some stuff with :

sudo "echo 'find | grep | rm|' " >> sudo, and variations there of but they aren't working.

I'm hoping to get a work around?

Thanks everyone!

---

### Post by hakermania on 2012-09-04
Welcome to the forums!

The command 'find' can accept as argument another command to execute on the found files. An example in your case would be:
```

find . -name "*test*" -exec rm -r {} \;

```
This will delete all the files&folders that contain the word 'test' inside their filenames. But, be extremely careful with this, it will delete your files ***_permanently_***.

So, **use with caution**.

If you need super user permissions in order to delete these files, then run the above 'find' command with sudo.

---

### Post by drmrgd on 2012-09-04
> **hakermania said:**
> Welcome to the forums!

The command 'find' can accept as argument another command to execute on the found files. An example in your case would be:
```

find . -name "*test*" -exec rm -r {} \;

```
This will delete all the files&folders that contain the word 'test' inside their filenames. But, be extremely careful with this, it will delete your files ***_permanently_***.

So, **use with caution**.

If you need super user permissions in order to delete these files, then run the above 'find' command with sudo.

Dang!  Beat me to the punch!  

I'll just add if there are not too many files and you want to check each as it's being deleted, you can add the interactive option to rm:

```
find . -iname "test*.txt" -exec rm -ri {} \;
```

If you want to do a "dry run" to see what would be deleted, then you can use the 'echo' that you had suggested earlier:

```
find . -iname "test*.txt" -exec echo rm -r {} \;
```

---

### Post by doktorOblivion on 2012-09-04
What I always use, since I can test before hand what files its actually finding is something like the following:

find . -name '*mysearch*' > out

I review out, if it looks okay, I then use:

find . -name '*mysearch*' | awk '{ print $1; system("sudo rm -f " $1); }'

This will print and then remove each file that is piped into the awk command.

USE with extreme caution.

There are many other ways of doing this, I find piping it into awk gives me more control.

---

### Post by Vaphell on 2012-09-04
why not use -delete flag and skip piping entirely?

```
find ..... -print -delete
```

---

### Post by MusicalRobots on 2012-09-04
Thanks everyone, got it working, much appreciated!

---

