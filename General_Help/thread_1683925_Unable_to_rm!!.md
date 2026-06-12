---
title: "Unable to rm!!"
date: 2011-02-08
forum: General Help
---

### Post by manolomanolo on 2011-02-08
Hi to all.

I am unable to remove a folder containing a very huge number of files. All the files start with the "*run*" word. For example, the folder can contain the *runUP001.txt* file and *runDOWN611902.txt* files.
Actually trying to count the number of files into that folder is practically impossible since *ls*, the file properties, and so on are unable to list or count those files.

In fact, running:
```
rm -f . *
```
or
```
ls *
```
give the same result: ```
Argument list too long
```

Even running the same commands with "*sudo*" does the job.
When trying to remove the directory too (with all the included files), it hangs instead.

After Googling, I tried some old workarounds like
```
find . -iname run* | xargs rm
```
But I get almost the same result since *find* is not able to list the files into that folder.

Another workaround should be [modifying the related **kernel limit** on the ARG_MAX value]("http://www.ducea.com/2006/05/24/binrm-annoying-limitation-argument-list-too-long/") or trying to [delete a small group of files instead of deleting all them at the same time]("http://www.bigsoft.co.uk/blog/index.php/2008/08/09/rm-argument-list-too-long").
In the first case, should I recompile the kernel?
In the second case, what about finding any group (or even all of them!) still overcoming that default kernel limitation?

Thanks for your attention. Best regards.

PS: Nautilus cannot show all the files (takes too long without completing the listing operation), but it can list some of those files as soon as it reads from that folder, but it is not reasonable to ask user to select and remove those files manually (they are a very huge number of files and it is not good to spend your DAYS in waiting Nautilus for listing them all!!!).

Ubuntu 10.10
kernel 2.6.32-22-generic

---

### Post by Lampi on 2011-02-08
try find . -regex './run*' -exec rm -v {} \;

---

### Post by HermanAB on 2011-02-08
rm -rf wherever/a*
rm -rf wherever/b*
rm -rf wherever/c*
...

---

### Post by Bucky Ball on 2011-02-08
> **HermanAB said:**
> rm -rf wherever/a*
rm -rf wherever/b*
rm -rf wherever/c*
...

Like Herman says. You can't remove a folder if there's files in it. So:

```
sudo rm -rf /foldername
```Be very careful! Make sure you give the exact path to the folder as this command removes that folder and all files in it! You can imagine the consequences if you got the wrong one. ;)

---

### Post by manolomanolo on 2011-02-08
> **HermanAB said:**
> rm -rf wherever/a*
rm -rf wherever/b*
rm -rf wherever/c*
...

Unfortunately, as I said:
> In the second case, what about finding any group (or even all of them!) still overcoming that default kernel limitation?

I am searching for a method that results to be 100% sure. That workaround supposes that the number of files beginning with "a" is lower than that kernel limit. That is, the problem persists!

---

### Post by manolomanolo on 2011-02-08
> **Lampi said:**
> try find . -regex './run*' -exec rm -v {} \;

it seems that the command with correct quoting is:

```
find . -regex `./run*` -exec rm -v {} \;
```

However, it hangs... on a Sun Ultra 24 Workstation, Intel Core 2 Duo 3.16GHz with 8GB of RAM and 6MB L2 cache!!!

---

### Post by Lampi on 2011-02-08
> **manolomanolo said:**
> it seems that the command with correct quoting is:
```
find . -regex `./run*` -exec rm -v {} \;
```
However, it hangs...3.16GHz with 8GB of RAM and 6MB L2 cache!!!
nope, it's supposed to be apostrophes, not backticks. I noticed a missing dot in front of the wildcard, this one should be responsible for your trouble. Also note the maxdepth addition, so find will not travel more than one level of directories, type f will make sure to list files only:
```
find . -maxdepth 1 -type f -regex '^./run.*'
```
Try to figure out a working find line without the exec part first, once you have it, add the -exec part again.

---

### Post by manolomanolo on 2011-02-09
Well done!

The following command should be enough in my case
```
find . -regex '^./run.*' -exec rm {} \;
```

I am still not able to tell you if it does the job since it is taking long time in removing the files one by one. Yes... you got it... it is removing them! :guitar:

I'll tell you something when it finishes working!
Thanks a lot!

---

