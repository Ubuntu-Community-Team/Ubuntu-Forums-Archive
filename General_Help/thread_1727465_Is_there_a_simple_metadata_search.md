---
title: "Is there a simple metadata search?"
date: 2011-04-12
forum: General Help
---

### Post by A.M.W on 2011-04-12
Hi, I was wondering if there is a simple way to find a file by searching for a word in the metadata?
I have lots of CD's containing photos which have information about them stored in the metadata, eg location it was taken, who is in the picture etc. When using Win XP I can put a disc in and search from Windows Explorer for a word, for example "John", then it will quite quickly list all the files with "John" in the metadata or file name. Searching with Nautilus only shows files with a match in the file name not the metadata. 

I have played around with Beagle, Tracker & recoll and they will sort of work but you have to index/create database first before it will find them. Is there a way of searching without indexing first? I just want to tell it what location and what keyword and have it search for the matches.


Cheers

Adrian

---

### Post by earthmeLon on 2011-04-12
This is an example on how to do similar with pdf files and their 'subject' and 'author' tags.  Check it out and let me know if it's what you're trying to accomplish.

[http://askubuntu.com/questions/31869/how-to-search-pdf-files-by-their-metadata](http://askubuntu.com/questions/31869/how-to-search-pdf-files-by-their-metadata)


Hopefully gnome-do and synapse will eventually handle meta-data.


Edit:  I guess you already tried this one.  Didn't realize it was the same name.

Just so you know, anything that doesn't create a database is going to 1) task your hdd 2) be much slower.  Why is it that you would prefer not having a database?

---

### Post by A.M.W on 2011-04-13
> **earthmeLon said:**
> 

Just so you know, anything that doesn't create a database is going to 1) task your hdd 2) be much slower.  Why is it that you would prefer not having a database?



Thanks for the reply. I don't want the database method as they don't support removable media very well. I know Beagle does support removable media but it is not automatic, you have to do some command lines to tell it to index a disc and another command line before you can remove the disc etc. As for being much slower, that's OK, Windows Explorer takes about 20sec to search a CD full of photos which is fine by me.
Having said that, if anybody has come up with a way of automating the process for beagle, eg launch a script to quickly index the CD etc and maybe another script to remove the index when you remove the disc that would be great.

Cheers
Adrian

---

### Post by A.M.W on 2011-04-15
I have been playing around with Beagle some more and it looks like I should be able to create a static index for each CD then load this index into beagle when I want to search to CD. I say "should" as so far I have been unable to do this. Is there any documentation on how to do this? The beagle website doesn't explain it very well.

Adrian

---

