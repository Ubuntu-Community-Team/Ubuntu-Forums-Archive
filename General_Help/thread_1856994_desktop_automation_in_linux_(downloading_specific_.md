---
title: "desktop automation in linux (downloading specific files)"
date: 2011-10-09
forum: General Help
---

### Post by Martiini on 2011-10-09
I want to automate uubntu to download, move and delete specific files
specifically, download .torrent files named *ubuntu* from [http://linuxtracker.org/](http://linuxtracker.org/)
I think this can be accomplished with some bash script, cron, transmission or maybe firefox imacros, rss, vuze .. 

if anyone has idea, please post solution

---

### Post by papibe on 2011-10-14
This is what I would do:

Analyze the html code of that page. If it were very simple, I would use wget to get the page, and then a combination of sed, awk, or grep inside a bash script.

If it were a complex page, I would use python with a library called [BeautifulSoup]("http://www.crummy.com/software/BeautifulSoup/") that is designed to parse html code.

Once I got the *ubuntu*torrents links, I would use transmission-daemon as a back end, and load the torrents using transmission-remote:
```
$ transmission-remote -n user:password -a url
```

Just some thoughts,
Regards.

---

### Post by Martiini on 2011-10-22
> **papibe said:**
> This is what I would do:

Thanks!
same subject has been resolved here
[http://ubuntuforums.org/showpost.php?p=7949235](http://ubuntuforums.org/showpost.php?p=7949235)
[http://ubuntuforums.org/showthread.php?t=848652](http://ubuntuforums.org/showthread.php?t=848652)

---

