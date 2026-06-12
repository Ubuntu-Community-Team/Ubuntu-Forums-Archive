---
title: "Ubuntu search capability"
date: 2010-05-10
forum: General Help
---

### Post by julianb on 2010-05-10
I have tried to use the search feature of Ubuntu 10.04 and previous versions, and have not found that it measures up well against OSX or Windows. 

Here's what I want, that OSX and Windows 7 provide:

a program that indexes files as they are created, so that file searches take place almost instantly. I want it to work without any fuss. I am not that interested in Google Desktop or similar, where a newly created file might not be indexed until 15-45 minutes after it's created.

I've tried tracker and beagle and they did not seem to be working properly. What's the best choice for simple, out-of-the-box operation without serious bugs? How do you get it to return search results correctly?

No fancy features required.

---

### Post by NT4usB on 2010-05-10
afaik, all the current releases have an indexer running by default... I go to great effort to hunt them down and turn them off since they suck resources on my anemic machines.
Never found much use for the graphical search options. I use ```
 locate bla
``` from a terminal when I want to find something.
I haven't tried the graphical search since Dapper days so it may be better now.
Keep in mind, some directories are (were?) omitted from indexing by default, /media for one. Searches won't find anything there since it's not indexed. crs has set in again and I can't remember the name of the file to edit to remove this omission.

...don't get me going about Windows search, when the file I'm looking for is right in front of my eyes in explorer yet Windows search can't find it.

---

### Post by WorMzy on 2010-05-10
Running 'sudo updatedb' forces the locate database to be updated. According it it's man page, cron runs the update automatically once per day.

---

