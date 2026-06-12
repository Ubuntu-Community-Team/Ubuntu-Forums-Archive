---
title: "'find' command returns different results"
date: 2011-03-20
forum: General Help
---

### Post by porchrat on 2011-03-20
I'm very confused by this.

I have 2 machine both running Ubuntu 10.04 64bit. When I move a directory from one machine to another and try run 'find <directory name> -type f' I get the returned list with the files but they're in different orders.

Why would the find command return the list in 2 different orders on different machines?

---

### Post by TeoBigusGeekus on 2011-03-20
What do you mean by two different orders?
Could you give us some output from the find commands?

---

### Post by porchrat on 2011-03-20
I mean that the outputs are not in the same order. Unfortunately I don't think I'm permitted to show you the outputs because it isn't my data :(

For example lets say I have files foo, bar, jim and jam contained within directory1.

One machine outputs the following list:

```

/home/porchrat/data/directory1/foo
/home/porchrat/data/directory1/bar
/home/porchrat/data/directory1/jim
/home/porchrat/data/directory1/jam

```

and the other one outputs this:

```

/home/porchrat/data/directory1/bar
/home/porchrat/data/directory1/jam
/home/porchrat/data/directory1/foo
/home/porchrat/data/directory1/jim

```

Literally what I mean. The outputs are in a different order when the filesystem, OS version and directories are identical. I just don't get it. They don't miss any files. They just list them in different orders. I've never seen anything like it.

---

### Post by TeoBigusGeekus on 2011-03-20
I don't know how find sorts its results, but you can pipe your command with
```
|sort -h
```
so that the output is sorted by size.

---

### Post by porchrat on 2011-03-20
> **karmelon said:**
> Sorry fully do not understand

I know lol neither do I.

Basically what I'm seeing is:

identical input --> find command --> different output

:confused:

I'm starting to think there must be something wrong with one of the systems. Maybe one is storing the files in a different order on disk because it doesn't seem that the find command returns things in alphabetical order anyway so I assume it returns the files as it encounters them on disk.

---

### Post by porchrat on 2011-03-20
It isn't even consistent when you look at recursion.

So for every single subdirectory the orders of the files within those subdirectories (as they appear in the 'find' command's returned list) are different despite the contents being identical. I am totally blown away by this.

---

### Post by skada on 2011-03-20
try to find inodes of each file you mention .

---

### Post by porchrat on 2011-03-20
> **skada said:**
> try to find inodes of each file you mention .

This sounds like it is connected to the way the system is storing the files. This would make sense and it is what I'm thinking too. I don't think the problem is with the 'find' command. In fact I'm certain it isn't a problem with the 'find' command because I just went and used another program (written in Java) I wrote a while back that does the equivalent of the 'find' command in that it recursively lists files. I've experienced the same problem. Outputs identical to the 'find' command but each machine produces results in a different order.

Looking at that it must be a case of the machines storing the files in different orders.

How would I go about finding the inodes? (EDIT: looked it up apparently I can use 'ls' with a -i option)

---

### Post by porchrat on 2011-03-20
I looked into inodes using 'ls -i'.

I tried looking at the first result from outputA and a few of the results following it. I then checked to see where in outputB those files were arranged and checked their inodes.

It didn't reveal much. Neither find command seems to return the files in any particular order that relates to inodes. They're all over the place.

I really don't get it :(

---

### Post by TeoBigusGeekus on 2011-03-20
IMO, I think you worry too much. :popcorn:

I'd also love to learn why it happens, but not that it is a problem...

---

### Post by porchrat on 2011-03-20
> **TeoBigusGeekus said:**
> IMO, I think you worry too much. :popcorn:

I'd also love to learn why it happens, but not that it is a problem...

LOL it is a problem. That list forms the input for an application I run and I'm not allowed to sort the stuff.

Normally I wouldn't be worried about it.

---

### Post by The Cog on 2011-03-20
Does **ls** show the order differently on the two mmachines? If so, then the problem is probably in the collation settings on the machine, which is somehow connected with the regional settings. You'll have to google for something like "linux collate sort order" - I can't remember the details myself.

It might be interesting to use the command ```
ls -l -U
``` which outputs the file list unsorted on the two machines, and see if the files are really stored in the same order on the two filesystems.

In my opinion, you should never rely on the order in which files are stored on disk as simply editing files can change the order that their entries are stored in the directory. That said, if you really must have the files in the order they are currently stored in the on-disk directory structure, all I can think of is using **ls -U** and recursively walking the tree. And you should expect that the file order will change if you replicate the folder structure to somewhere else in any other way than by making a filesystem image copy. cp, tar, rsync etc are all likely to not copy files in the order they appear in the raw filesystem directory.

---

### Post by porchrat on 2011-03-21
The Cog you are spot on!

I checked the organisation of the systems using "ls -lU" and the order of the files on disk directly corresponds to the way in which they are returned by find. I am so glad that I can finally see a pattern and at least know what the problem is! Thank you so much you have brightened my day considerably!

When you say it is connected to the regional settings is that the same thing as the locale settings?

I recall that I did have an issue with the locae settings when I first installed the system and I had to use the liveCD to edit /etc/default/locale to get Ubuntu to load a workable locale so I could at least start working on other things the system needed. I didn't think it was related so I didn't mention it.

When I check the locale using the "locale" command it tells me they are set to the same locale (en_ZA (the system needs to run on ISO-8859-1 by default)).

If this is going to become a problem I may have to ask if I can't reorder these files. Any idea how I would go about getting the files to store in the same order first? I'm amazed by this because it has never been a problem before. Before the systems just stored everything in the same order each time by default.

---

### Post by The Cog on 2011-03-21
> Thank you so much you have brightened my day considerably!Oh good. It's nice to feel I brightened somebody's day.
> When you say it is connected to the regional settings is that the same thing as the locale settings?Yes. I know the environment variable LC_COLLATE is involved but I don't rememer the details.

As I say, the only way I can think of to copy the files in the right order is to write a script that does ls -U in the root directory and copies those files, then for each of those files that is itself a directory, recursively copy that the same way. This is because (I thnk), cp and rsync copy the files in aplhabetic order.

---

