---
title: "How do I do a mass delete based on the results of a search?"
date: 2011-12-05
forum: General Help
---

### Post by Pearl E on 2011-12-05
I'm a recent Windows escapee, so I'm still getting the hang of this OS freedom thing. It's nice to have more control over what my computer is doing, that is, except when I can't figure out how to make it do what I want.

How do I do a search by file-type / file location and then mass delete the files I find?

I've got 14,000 files to sort, and about a quarter of those have to be found and deleted. I'm about to go insane trying to do it by clicking though the folders and menus for each and every file.

I'd really appreciate your help!

---

### Post by nothingspecial on 2011-12-05
You would use the find command, but you **need** to get it right.

What are the search parameters?

---

### Post by pholden on 2011-12-05
You can use *find* with the *-exec* argument to delete each file as it's found;
```
find /path -type f -iname "*.jpg" -exec rm -f {} \;
```

Or you can find all of them, and delete the lot in one go;
```
find /path -type f -iname "*.jpg" -print0 | xargs -0 rm -f
```

The [man page for find]("http://linux.die.net/man/1/find") would be a good starting point to read about the various arguments.

---

### Post by ratcheer on 2011-12-05
Yes, find is the best way to do it. For example, at work I had a folder that had hundreds of files added to it every day. I ran this command to delete all files that were more than 10 days old. I ran it in the directory where the files resided.

```
rm `find . -mtime +11`

```As Pearl E said, you have to be very careful to first ensure that the find command gets the files you want and only the files you want.

Tim

---

### Post by aeiah on 2011-12-05
you can use find in several different ways. the following way is nice:
```

find . -type f -iname "*.jpg" -print

```
this just prints the outcome of the search. useful for checking. when you're sure, you can change -print to -delete:

```

find . -type f -iname "*.jpg" -delete

```

---

