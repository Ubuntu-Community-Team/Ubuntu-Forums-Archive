---
title: "Shrinking main filesystem"
date: 2011-02-15
forum: General Help
---

### Post by ZGruk on 2011-02-15
For awhile now I've had a problem where my main filesystem periodically fills up and give me a warning. I thought at first, and I think I was partially correct, that I was just downloading too much stuff. Later I discovered that a hidden file called XOrg.conf or something similar was becoming very large (2 or more GB). This I deleted whenever it came up, and thus freed up a bunch of space. Now, however, I'm getting these warnings again. There is no large XOrg file and yesterday I cleaned my system up to where I had over 6 GB free. I have not downloaded or transferred files to it since. I am noticing, when I run Disk Usage Analyzer, that while it says that I'm using 39.7 out of the 40 GB of my main filesytem, when it finishes scanning it says that / is 28 GB. Where is the other 12 GB going? I'm getting dangerously low on space (300MB).

---

### Post by PaulReaver on 2011-02-15
so basically you're filling up your hard disk???



you could try "bleachbit" to recover some space

$ sudo apt-get install bleachbit

it can clear out a lot of junk from a system.... kinda like ccleaner,
it can delete old internet cache and apt's cache (which can recover a lot of space) it can remove old log files, it can also remove unused language packs :) 

make sure not to untick your language though (best to leave english as well) 

and _[COLOR="Red"]double check[/COLOR]_ everything before hitting the delete button

hope it helps

---

### Post by ZGruk on 2011-02-15
Turns out all it really needed was for me to restart the computer, and it went back to the 11 GB free it was supposed to show.

Glad I have bleachbit now, though, it did free up 3 extra GB I wouldn't have gotten otherwise

---

### Post by PaulReaver on 2011-02-15
3gb!!! not bad :)

---

### Post by ZGruk on 2011-02-21
Well, I said it was solved, but I spoke too soon. After I ran Bleachbit and restarted the computer, it did free up all that "phantom space" at first. Later, however, it came back. I now have nearly 10 GB missing. I have attached a screenshot illustrating what I mean. It's apparently having graver effects now as well. My computer locked up this morning and when I tried to restart it it spit errors related to the file-system and forwarded me to a command-line interface. I booted off a cd and ran fsck on the main file system, but it didn't find any errors, and when I tried to boot again it worked. I'm still missing 10 GB of space though, and I'm afraid if this happens again, it might not come back. I'm backing things up just in case

---

