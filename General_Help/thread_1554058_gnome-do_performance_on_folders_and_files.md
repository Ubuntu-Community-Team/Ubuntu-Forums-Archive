---
title: "gnome-do performance on folders and files"
date: 2010-08-16
forum: General Help
---

### Post by g.a. on 2010-08-16
Hi,

I have a very simple question concerning gnome-do.

I have configured to search for folders and files, starting from my home directory and going deep up to 20 directories.

The program gives me a message that it is indexing too many files, I guess it is giving up? it basically do not find some of the files/folders I try.

Any suggestion? thanks in advance

Also, any suggestion for any alternative launcher application to try?

the version is 0.8.2 for ubuntu 9.10

---

### Post by stinkeye on 2010-08-16
Try kupfer.
Not as pretty but better in my opinion.
One thing that might throw you at first is that when your entering a search
if you pause too long between key strokes the new entry becomes the first letter of your search.
It's a bit hard to explain but you'll see what I mean if you use it.

It's available in the software centre but if you want the latest version 
you may want to use the kupfer ppa.
```
sudo add-apt-repository ppa:kupfer-team/ppa

sudo apt-get update

sudo apt-get install kupfer
```

---

### Post by g.a. on 2010-08-17
thanks, i just installed and i will try it together with gnome-do for the next days.

best
g.

---

### Post by glocal on 2010-10-09
> **stinkeye said:**
> Try kupfer.
Not as pretty but better in my opinion.


Thanks for that. Much better than gnome do. But I must be doing something wrong. It doesn't detect files in the set directories. I know I have lots of .pdf and .doc files in directories and sub-directories but it will not locate them. Either it takes a *very* long time to build the initial database (unlikely, because it doesn't seem very busy indexing) or it doesn't look into sub-directories, which would be a huge problem, or perhaps a necessary plugin is disabled. Strangely, it will only detect files in a very specific subdirectory. Any ideas?

---

### Post by stinkeye on 2010-10-10
I use the locate files plugin.

Open kupfer.
Hit the "." key for text input.
Type in the name of the file your looking for.
Hit the tab key then down arrow to the Locate Files plug-in and hit enter.

Then if you hit tab again you can down arrow to various options like
open and reveal.

In kupfer preferences in the catalog tab it tells you why kupfer doesn't carry a large catalog of objects.

---

### Post by glocal on 2010-10-10
Ah, yes, it sort of works. It locates a lot more than before, but still it misses too many useful files and comes up with many irrelevant hits. I suppose relevance could improve if I changed the paths it scans, but it would be much better if there was a way to narrow the search on a case-by-case basis. Surprisingly, it returns 0 hits for words that should produce 100s of hits. Sometimes, I type in a word (eg "abc"), press Tab to trigger Locate and then it shows a message in the left pane saying 'Type to search...s for "abc". I suspect the missing bit is 'results', but I am not sure what it means. The moment I press a key, any key, (eg 'a'), it says 'No matches in ..."abc" for "a"'. The way its locate works is very awkward, and inferior to that of gnome-do (or Launchy), but avoiding indexing of 1000s of files improves performance. Unless I figure out how to improve results, I think I'll stick with Nautilus's Locate for files as it is so fast and effective, and Kupfer for the rest. 

I know Kupfer is an integrator, not an indexer, but the distinction (like many other things in Kupfer) is not very clear. I had assumed it claimed it was not an indexer because it didn't index content (which is fine -- I use Recoll for content indexing). Conversely, surely integration involves some indexing.

---

### Post by Aksoy on 2010-11-19
You can use Gnome Do to search almost every file on your system. Instead of using the Files and Folders plugin, use Locate Files. And I regularly use the command below in order to be able to see every file on my system using Gnome Do.

sudo updatedb

If I can't see the files I'm looking for or every time I make major changes to my files, I type this code then I can locate my files using Gnome Do. It works for me.

---

### Post by g.a. on 2010-11-20
I have a problem with the "locate" command of gnome-do.

Here is an example, I search for all directories/files with the characters "tesan" inside.

I run gnome-do associated to a shortcut.

Despite the 5 digits search a lot of files show up (201 entries).

In order to run the "locate" command I have to scroll down all the entries with the down arrow. this is time consuming and slower with respect to the "search for files" command that I also associated to a shortcut.

Is there a magic key that just jumps me to the "locate" ?

thanks,
g.

---

### Post by Aksoy on 2010-11-20
Well I'm not really sure if you can do such thing but I sometimes end up with much more results than expected too. That's why I use Gnome-Do when I'm trying to locate a bit specific files or folders. Other than that I can recommend you to use the Search for files command. Since it allows you to enter much more parameters (Size, Modification date, etc.) which makes it easier for you to narrow down your search results.

---

