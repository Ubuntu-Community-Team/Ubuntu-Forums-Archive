---
title: "Command help on folder and file size display"
date: 2011-09-27
forum: General Help
---

### Post by urocks on 2011-09-27
Hi,

I wanted to display folder and file sizes in a given folder in descending order. 
After searching for a while I found two commands from following article.

[http://www.ducea.com/2006/05/14/tip-how-to-sort-folders-by-size-with-one-command-line-in-linux/](http://www.ducea.com/2006/05/14/tip-how-to-sort-folders-by-size-with-one-command-line-in-linux/)

(1) du -s * | sort -nr | cut -f 2- | xargs -i du -sh {}

This one displays files and folders but not hidden files or folders.

(2) du -s */ .[^.]*/ | sort -nr | cut -f 2- | xargs -i du -sh {}

This one displays folders and hidden folders but not individual files.

I need a command that displays folders, files and hidden content.
Any help given is much appreciated.

---

### Post by Leppie on 2011-09-27
how about this:
```
ls -alrR ./ 
```

---

### Post by urocks on 2011-09-27
Thanks for the reply Leppie.

But this command didn't serve my purpose.

---

### Post by drmrgd on 2011-09-27
> **urocks said:**
> Thanks for the reply Leppie.

But this command didn't serve my purpose.

You may need to elaborate on what is wrong with the command so that we can offer more advice.  What is it not doing that you'd like it to do?

---

### Post by brucehohl on 2011-09-27
This might get you close enough:
$ du -h --max-depth=1 .

---

