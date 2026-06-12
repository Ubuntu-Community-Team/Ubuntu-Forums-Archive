---
title: "how do I search inside of zip files"
date: 2010-01-06
forum: General Help
---

### Post by Eugene_Bondarenko on 2010-01-06
Hi,

When I was on Windows, I had a tool that was set to run incremental backups every day. It used zip to compress backuped files. Later I moved all important stuff to Ubuntu and formatted my Windows HDD. Now I've realized that I forgot to move some important stuff and it was erased. It still can be found in those backups though. 
The problem is to find it now. :) Manually going through hundreds of zips will be extremely painful. So I wonder if there is any way to for example run a search for a folder named 'xyz' in the specified folder that has all those zips and instruct the search tool or script to enter those archives and search them recursively too.

---

### Post by phDaemon on 2010-01-06
[http://www.cyberciti.biz/faq/unix-linux-grepping-compressed-files/](http://www.cyberciti.biz/faq/unix-linux-grepping-compressed-files/)

From Article:
> Linux and UNIX comes with z-commands. zgrep invokes grep on compressed or gzipped files. All options specified are passed directly to grep.
To search .gz file called test.gz, enter:
```

$ zgrep 'word-to-search'  /path/to/test.gz
$ zgrep 'GET /faq/a-long-url/'  /path/to/access.log.gz

```You can run zcat command to display file on screen:
```
$ zcat file.gz
```You do this on the terminal.

BTW: As always, you can always look in google, thats what i did ;)

---

