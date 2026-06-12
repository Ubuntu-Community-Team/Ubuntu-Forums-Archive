---
title: "Nautilus Templates Don't Work"
date: 2006-05-24
forum: General Help
---

### Post by zeasier on 2006-05-24
Unfortunately I don't have much information on this problem. I create text files in ~/Templates. They show in Nautilus's create documents sub menu, but when I select them nothing happens.

Currently I'm using Breezy, the problem also occurs in Dapper. From what I've read, many people seem to be using this feature without any problems.

One thing about my system that is less common it that /home is mounted via nfs. Can anyone with a similair setup get Nautilus templates to work?

---

### Post by Tiede on 2006-05-24
That sounds odd. I don't remember having to do any tweaks to have them work... I would suggest maybe saving a blank file from the program you want to create a Template for in ~/Templates...
but AFAIK, it shouldn't matter.
Just as a precaution, make sure you have full ownership rights on the files. --And that the files are actually in ~/Template**s** and not ~/Template. I made that omission myself and was startled for a while trying to figure out what went wrong. :D
Lastly, I do not know much about the Templates folder, but i fail to see how the filesystem type will be of any relevance... Sorry I don't have much more.

---

### Post by zeasier on 2006-05-24
I just unmounted /home and created a local /home/user. It seems templates do work on my system as long /home is not running nfs.

So how can I get templates working with nfs? If I'm not missing something and it really doesn't work, maybe this is a bug I should file.

---

### Post by zeasier on 2006-05-24
If anyone else is having this problem, I found a temporary solution. Create directory some where in the local file system. Then, link it to ~/Templates using ln -s.

---

