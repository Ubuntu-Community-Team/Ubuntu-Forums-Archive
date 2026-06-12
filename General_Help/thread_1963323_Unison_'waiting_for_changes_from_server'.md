---
title: "Unison 'waiting for changes from server'"
date: 2012-04-22
forum: General Help
---

### Post by christovic on 2012-04-22
Hi, I have a desktop, and a netbook, and would like to keep them in sync using Unison. I tried using the gtk gui, but it hung on the 'waiting for changes from server', so had to kill it. I read up about it and since the directory i want to sync is ~30GB, on the first time, it needs to archive things. I found that you need to run the -path directive to get them to sync the first time. I can't figure out how to use it! I type in:
```
unison Sync -path xxx
```
('Sync' is the profile name)
And then it just spits out this:
```
daniel@daniel-desktop:~$ unison Sync -path xxx
Contacting server...
daniel@**********'s password: 
Connected [//daniel-desktop//home/daniel -> //daniel-ubuntu//home/daniel]
Looking for changes
  Waiting for changes from server
Reconciling changes
Nothing to do: replicas have not changed since last sync.

```
This is just after I have added a new document straight in the home directory
What's going on?

---

### Post by Habitual on 2012-04-22
```
cat ~/.unison/Sync.prf
```
output please.

---

### Post by christovic on 2012-04-22
```
daniel@daniel-desktop:~$ cat ~/.unison/Sync.prf
### ROOT SYNC PATHS ###

# first root is my home directory on this laptop
root = /home/daniel/

# second directory is my desktop's home folder over SSH 
root = ssh://daniel@*********//home/daniel/

### PATHS TO SYNCHRONIZE ###



ignore = Name .*



```

---

### Post by christovic on 2012-04-22
Also, if I enter
```
unison -path Sync
```
i get 
```
daniel@daniel-desktop:~$ unison -path Sync
Usage: unison [options]
    or unison root1 root2 [options]
    or unison profilename [options]

For a list of options, type "unison -help".
For a tutorial on basic usage, type "unison -doc tutorial".
For other documentation, type "unison -doc topics".
```
Not making much sense to me

---

### Post by dcstar on 2012-04-23
> **christovic said:**
> Hi, I have a desktop, and a netbook, and would like to keep them in sync using Unison. I tried using the gtk gui, but it hung on the **'waiting for changes from server'**, so had to kill it. I read up about it and since **the directory i want to sync is ~30GB**, on the first time, it needs to archive things.
........

Don't "kill" it, wait for it to run as it has to scan all 30GB of data.

[https://alliance.seas.upenn.edu/~bcpierce/wiki/index.php?n=Main.UnisonFAQTips](https://alliance.seas.upenn.edu/~bcpierce/wiki/index.php?n=Main.UnisonFAQTips)

---

### Post by christovic on 2012-04-24
Mmmm,I read that, although this is what has got me posting here:
> While you're getting things set up, you'll probably save time if you start off focusing Unison's attention on just a subset of your files, by including the option -path some/small/subdirectory on the command line.
I'm not quite sure how to get that working...

---

### Post by Habitual on 2012-04-24
Is "ignore = Name .*" even valid syntax?

unison --help here shows 
"-ignore xxx" using unison version 2.32.52

---

### Post by christovic on 2012-04-24
Seemed to be working for me, when I ran the sync it seemed to skip all hidden directories.

---

