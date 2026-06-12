---
title: "searching, grep, tracker, etc.??"
date: 2010-05-09
forum: General Help
---

### Post by ClarkePeters on 2010-05-09
system: Ubuntu Hardy Heron

can somebody explain to me about the different methods of searching file content on Ubuntu?  I have had ubuntu for many years now but never had the need, as I could pretty much remember where things were. Now, I'm older, more forgetful, and as an educator, have amassed a Documents folder/subfolders of nearly 50,000 files (49,585 @ 9.6 gb to date, to be exact).

I know there's grep, and the menu "places->search for file", and also Tracker.

Is there a gui for grep? I couldn't find one. Grep is not index based, right?
Also, exactly how does "places->search.." work, like grep or off of a super index like Tracker, and as far as Tracker, it is an indexed search engine, right? I have it turned off at present because in the past I felt that it slowed down my computer and at the time I wasn't using it. Is there some advantage here?

So, I don't exactly know what I need but I do know I need to be able to search the contents of my files and get semi-decent hits, and I don't want something that boggs down my system nor will take a week to get indexed.

Any suggestions? Anyone with massive files content have a preferred method? Any help at all will be appreciated.

---

### Post by ajgreeny on 2010-05-09
It sounds to me as if tracker is what you want.  Be warned, though, it can take a lot of machine resources when it is indexing.  It does, however, find all word content in open office documents, spreadsheets, text files and all file names quickly and easily, but at the moment does not search email messages in Thunderbird; I don't know if it does in Evolution, as I have never used that.

---

### Post by sgage on 2010-05-09
I have found Recoll to be the best indexing file search utility. I've tried Tracker and Beagle, but I found them to be less than reliable and very demanding of resources. Recoll is fast and thorough, and can be set up to index various file formats (my document collection contains everything from ancient .wpd files through .doc and .sxw up to .odt).

Not sure if it will be in the Hardy repos, but maybe in backports. If not, you can probably download it from somewhere or other. A little googling will get the job done, I'm sure.

---

### Post by ClarkePeters on 2010-05-09
thanks all, since I'm somewhat familiar with Tracker, I'll first look into Recoll and see how it compares.

I also just came across "ack" which is kind of a modified grep, especially in that it can search through a directory and all subfolders automatically without the grep find/grep/xargs (which thank goodness I never used).
comparison from the website.
$ grep pattern $(find . -type f | grep -v '\.svn')
    versus
$ ack pattern

I'm a bit rusty on my perl regex but I think I can manage. I may still give Recoll a try if I get to a point where I can fee up my computer for indexing.

---

### Post by ClarkePeters on 2010-05-11
Recoll seems to be just what I needed. I like it because it's not in constant "index" mode so it doesn't use up my resources, I can just update the index when I feel like it. As far as indexing, it indexed my 50,000 files in record time compared to others I've tried in the past. I don't know exactly how long because I did walk away from the computer and I can't remember how much time elapsed so it could have finished in 30 minutes or 3 hours. At any rate, I've had some in the past that took days--literally. So it was plenty fast enough. A few test searches seems to be okay for what I need.

thanks all

---

