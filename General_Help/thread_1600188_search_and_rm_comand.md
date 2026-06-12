---
title: "search and rm comand"
date: 2010-10-18
forum: General Help
---

### Post by PrvSAT on 2010-10-18
Hi,

I run a lucid 10.05 on an Intel machine and it blows my mind off! 
I have had a problem with xbmc application and after removal I had some dependencies errors and I was suggested to remove everything related to xbmc.
So I did:
```
sudo apt-get remove --purge xbmc
and
sudo apt-get purge xbmc-*
sudo apt-get autoremove
then:
sudo update-apt-xapian-index
sudo apt-get install gdm
```reboot

At this point I opened nautilus in root mode:
```
sudo gksu nautilus
```And did a search in File System for xbmc and it did not find any file.

And here it comes... Then from terminal I did:
```
sudo locate xbmc
``` and found at least 10 entries... (???)
I said OK, I will delete them manually:
So for instance I did:
```
sudo rm -r /etc/apt/sources.list.d/team-xbmc-svn-ppa-lucid.list
```and the result:
```
rm: cannot remove `/etc/apt/sources.list.d/team-xbmc-svn-ppa-lucid.list': No such file or directory
```So what is happening? Why through root-nautilus would not find any xbmc file, nor if I try to purge it again (it tells me that there are no files with such name) and when I search the terminal I find at least 10 entries but I can not remove any of them?
Am I do dumb or what?

---

### Post by spikoley on 2010-10-18
Before running *locate* you need to run *updatedb*.  It probably is searching the database that is now out of date because you made changes.

```
sudo updatedb
```

```
sudo locate xbmc
```

---

### Post by PrvSAT on 2010-10-19
Thank you very much. I appreciate the help. It worked fine.

---

### Post by WorMzy on 2010-10-19
This won't help with your problem, but

> **PrvSAT said:**
> At this point I opened nautilus in root mode:
```
sudo gksu nautilus
```

There's no need for sudo in this statement.

```
gksu nautilus
```

Is all you need. :)

---

